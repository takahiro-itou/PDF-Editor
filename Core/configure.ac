
dnl----------------------------------------------------------------
dnl
dnl   Package Configurations.
dnl   パッケージ設定。
dnl

dnl
dnl   要求する autoconf のバージョンを指定する。
dnl

AC_PREREQ([2.68])

dnl
dnl   パッケージの情報を指定する。
dnl

AC_INIT(
    [SampleCore],
    [0.0.0],
    [BUG-REPORT-ADDRESS],
    [SampleCore])

dnl
dnl   ツールの出力ディレクトリを指定する。
dnl

AC_CONFIG_AUX_DIR([.Config])

dnl
dnl   適当なバージョンの automake を設定
dnl

m4_include([.M4/InitAutoMake.m4])

dnl----------------------------------------------------------------
dnl
dnl   プロジェクトの基本設定。
dnl

AC_CONFIG_SRCDIR([Makefile.am])
AC_LANG_CPLUSPLUS

dnl
dnl   デフォルトのコンパイルオプション
dnl

: ${CFLAGS:='-O0  -g  -D_DEBUG'}
: ${CXXFLAGS:='-O0  -g  -D_DEBUG'}

CFLAGS="${CFLAGS}  -std=c++11  -Wall"
CXXFLAGS="${CXXFLAGS}  -std=c++11  -Wall  -Weffc++"

dnl
dnl   Project Name Space.
dnl

SAMPLE_CNF_NAMESPACE=Sample
AC_SUBST(SAMPLE_CNF_NAMESPACE)

dnl----------------------------------------------------------------
dnl
dnl   ディレクトリ名。
dnl

m4_include([.M4/ConfigDirectory.m4])

MYAC_CUSTOMIZE_LIBRARY_DIR([Lib])
MYAC_CUSTOMIZE_BINARY_DIR([Bin])
MYAC_CUSTOMIZE_INCLUDE_DIR(
    [Include], [Sample], [.Config], [Config.h])

dnl----------------------------------------------------------------
dnl
dnl   ビルド環境の検査。
dnl

dnl
dnl   Check Programs.
dnl

AC_PROG_CC
AC_PROG_CXX
AM_PROG_AS
AC_PROG_RANLIB

dnl
dnl   Check Header Files.
dnl

dnl
dnl   Check Libraries.
dnl

dnl
dnl   Check Types.
dnl

dnl
dnl   Check Extra Compiler/Linker Options.
dnl

m4_include([.M4/CheckExtraFlags.m4])

m4_include([.M4/EnableCxx11.m4])

m4_include([.M4/CheckConstExpr.m4])
m4_include([.M4/CheckNullPtr.m4])
m4_include([.M4/CheckOverride.m4])

dnl----------------------------------------------------------------
dnl
dnl   Additional Packages.
dnl   外部パッケージの追加
dnl

m4_include([.M4/WithExtPkgs.m4])

MYAC_WITH_EXT_PKG(
    [CPPUNIT],  [cppunit],  [Path to cppunit],  [yes],
    [AMCNF_CPPUNIT_ENABLED],dnl
)
MYAC_SET_EXT_PKG_OPTIONS(
    [CPPUNIT], [cppunit], [lib], [include], [bin],dnl
)

dnl----------------------------------------------------------------
dnl
dnl   Outputs.
dnl   出力ファイルを設定する。
dnl

dnl
dnl   Basic Features.
dnl

AC_CONFIG_FILES([
    .CMake/Makefile
    .M4/Makefile
    Makefile
    Bin/Makefile
    Lib/Makefile
    Lib/.Config/Makefile
    Lib/Common/Makefile
])

AC_CONFIG_FILES([
    Include/Sample/.Config/ConfiguredSample.h
])

dnl
dnl   Test Festures.
dnl

AC_CONFIG_FILES([
    Lib/Common/Tests/Makefile
    Lib/Tests/Makefile
])

dnl
dnl   指定したファイルを生成する。
dnl

AC_OUTPUT

