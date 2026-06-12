---
title: "Error installing Cmake 2.6.4"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by mjb222 on 2009-06-01
Hi,
I'm rather new to ubuntu, and am getting an error when I do ./bootstrap for installing Cmake

matt@Lindy:~/Files/Programs/cmake-2.6.4$ ./bootstrap
---------------------------------------------
CMake 2.6-4, Copyright (c) 2007 Kitware, Inc., Insight Consortium
C compiler on this system is: cc 
C++ compiler on this system is: g++ 
Makefile processor on this system is: make
g++ is GNU compiler
g++ has STL in std:: namespace
g++ has ANSI streams
g++ has streams in std:: namespace
g++ has sstream
g++ has operator!=(string, char*)
g++ has stl iterator_traits
g++ has standard template allocator
g++ has allocator<>::rebind<>
g++ does not have non-standard allocator<>::max_size argument
g++ has stl containers supporting allocator objects
g++ has header cstddef
g++ requires template friends to use <>
g++ supports member templates
g++ has standard template specialization syntax
g++ has argument dependent lookup
g++ has struct stat with st_mtim member
g++ has ANSI for scoping
---------------------------------------------
g++ -I/home/matt/Files/Programs/cmake-2.6.4/Source   -I/home/matt/Files/Programs/cmake-2.6.4/Bootstrap.cmk -c /home/matt/Files/Programs/cmake-2.6.4/Source/cmake.cxx -o cmake.o
g++ -I/home/matt/Files/Programs/cmake-2.6.4/Source   -I/home/matt/Files/Programs/cmake-2.6.4/Bootstrap.cmk -c /home/matt/Files/Programs/cmake-2.6.4/Source/cmakemain.cxx -o cmakemain.o
...

g++  -I/home/matt/Files/Programs/cmake-2.6.4/Source   -I/home/matt/Files/Programs/cmake-2.6.4/Bootstrap.cmk  cmake.o cmakemain.o cmakewizard.o cmCommandArgumentLexer.o cmCommandArgumentParser.o cmCommandArgumentParserHelper.o cmDepends.o cmDependsC.o cmDocumentationFormatter.o cmDocumentationFormatterText.o cmPolicies.o cmProperty.o cmPropertyMap.o cmPropertyDefinition.o cmPropertyDefinitionMap.o cmMakeDepend.o cmMakefile.o cmExportFileGenerator.o cmExportInstallFileGenerator.o cmInstallDirectoryGenerator.o cmGeneratedFileStream.o cmGlobalGenerator.o cmLocalGenerator.o cmInstallGenerator.o cmInstallExportGenerator.o cmInstallFilesGenerator.o cmInstallScriptGenerator.o cmInstallTargetGenerator.o cmSourceFile.o cmSourceFileLocation.o cmSystemTools.o cmVersion.o cmFileTimeComparison.o cmGlobalUnixMakefileGenerator3.o cmLocalUnixMakefileGenerator3.o cmMakefileExecutableTargetGenerator.o cmMakefileLibraryTargetGenerator.o cmMakefileTargetGenerator.o cmMakefileUtilityTargetGenerator.o cmBootstrapCommands.o cmCommands.o cmTarget.o cmTest.o cmCustomCommand.o cmDocumentVariables.o cmCacheManager.o cmListFileCache.o cmComputeLinkDepends.o cmComputeLinkInformation.o cmOrderDirectories.o cmComputeTargetDepends.o cmComputeComponentGraph.o cmExprLexer.o cmExprParser.o cmExprParserHelper.o cmListFileLexer.o Directory.o Glob.o RegularExpression.o SystemTools.o ProcessUNIX.o String.o System.o -o cmake
cmSystemTools.o: In function `cmSystemTools::RemoveRPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, bool*)':
cmSystemTools.cxx.text+0x726): undefined reference to `cmELF::cmELF(char const*)'
cmSystemTools.cxx.text+0x752): undefined reference to `cmELF::GetRPath()'
cmSystemTools.cxx.text+0x789): undefined reference to `cmELF::GetRunPath()'
cmSystemTools.cxx.text+0x81c): undefined reference to `cmELF::GetDynamicEntryCount() const'
cmSystemTools.cxx.text+0x939): undefined reference to `cmELF::GetDynamicEntryPosition(int) const'
cmSystemTools.cxx.text+0x977): undefined reference to `cmELF::GetDynamicEntryPosition(int) const'
cmSystemTools.cxx.text+0x9c1): undefined reference to `cmELF::GetDynamicEntryPosition(int) const'
cmSystemTools.cxx.text+0xaa5): undefined reference to `cmELF::ReadBytes(unsigned long, unsigned long, char*) const'
cmSystemTools.cxx.text+0xb4a): undefined reference to `cmELF::~cmELF()'
cmSystemTools.cxx.text+0xb63): undefined reference to `cmELF::~cmELF()'
cmSystemTools.o: In function `cmSystemTools::CheckRPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
cmSystemTools.cxx.text+0x118d): undefined reference to `cmELF::cmELF(char const*)'
cmSystemTools.cxx.text+0x119: undefined reference to `cmELF::GetRPath()'
cmSystemTools.cxx.text+0x11ac): undefined reference to `cmELF::GetRunPath()'
cmSystemTools.cxxtext+0x121f): undefined reference to `cmELF::~cmELF()'
cmSystemTools.cxx.text+0x123: undefined reference to `cmELF::~cmELF()'
cmSystemTools.o: In function `cmSystemTools::ChangeRPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, bool*)':
cmSystemTools.cxx.text+0x138d): undefined reference to `cmELF::cmELF(char const*)'
cmSystemTools.cxx.text+0x13cd): undefined reference to `cmELF::GetRPath()'
cmSystemTools.cxx.text+0x1415): undefined reference to `cmELF::GetRunPath()'
cmSystemTools.cxx.text+0x19f7): undefined reference to `cmELF::~cmELF()'
cmSystemTools.cxx.text+0x1a10): undefined reference to `cmELF::~cmELF()'
cmSystemTools.o: In function `cmSystemTools::GuessLibrarySOName(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)':
cmSystemTools.cxx.text+0x1e4b): undefined reference to `cmELF::cmELF(char const*)'
cmSystemTools.cxx.text+0x1e6c): undefined reference to `cmELF::GetSOName(std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)'
cmSystemTools.cxx.text+0x203e): undefined reference to `cmELF::~cmELF()'
cmSystemTools.cxx.text+0x2057): undefined reference to `cmELF::~cmELF()'
cmSystemTools.o: In function `cmELF:perator bool() const':
cmSystemTools.cxx.text._ZNK5cmELFcvbEv[cmELF:perator bool() const]+0xd): undefined reference to `cmELF::Valid() const'
collect2: ld returned 1 exit status
make: *** [cmake] Error 1
---------------------------------------------
Error when bootstrapping CMake:
Problem while running make
---------------------------------------------
Log of errors: /home/matt/Files/Programs/cmake-2.6.4/Bootstrap.cmk/cmake_bootstrap.log
---------------------------------------------
matt@Lindy:~/Files/Programs/cmake-2.6.4$ 
matt@Lindy:~/Files/Programs/cmake-2.6.4$ 


Any help would be appreciated, thanks

---

### Post by Partyboi2 on 2009-06-02
Hi, if you don't mind an earlier version of cmake you can install it by searching for it in synaptic and installing it. If you need a later version I would suggest trying a 3rd party repo to install cmake 2.6.4. You can add [[COLOR=Blue]this[/COLOR]]("https://launchpad.net/%7Epgquiles/+archive/ppa") ppa repo if you want cmake 2.6.4.

If you are unsure on how to add the 3rd party repo let us know and someone will show you.

---

### Post by mldailey on 2009-08-26
I got a nearly identical error to this due to "dirty" cache files in the cmake directory. I'd tried to configure with "--qt-gui" before I realized I hadn't installed the qt4-dev - this produced qt4 errors. After fixing this, I started getting the errors above when configuring. After a bit a head-scratching, I deleted the cmake directory, untarred again, and everything worked fine.

Just for reference, here's what I did:

QT4:
$ sudo apt-get install libqt4-dev
$ sudo update-alternatives --set qmake /usr/bin/qmake-qt4

CMake:
$ wget [http://www.cmake.org/files/v2.6/cmake-2.6.4.tar.gz](http://www.cmake.org/files/v2.6/cmake-2.6.4.tar.gz)
$ tar zxf cmake-2.6.4.tar.gz
$ cd cmake-2.6.4
cmake-2.6.4$ ./configure --qt-gui
cmake-2.6.4$ make
cmake-2.6.4$ sudo make install

The system used was hardy 8.04.3 amd64

I hope this helps...

---

