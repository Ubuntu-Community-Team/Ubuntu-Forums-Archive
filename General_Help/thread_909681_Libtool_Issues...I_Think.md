---
title: "Libtool Issues...I Think"
date: 2008-09-03
forum: General Help
---

### Post by teddybouch on 2008-09-03
I pray your patience - I am a Mechanical Engineer working on a Master's degree developing a multi-robot system, and I want desperately to use Player/Stage/Gazebo for this project. Unfortunately, I am having a very hard time doing this because of what I think are issues in installing the dependencies. Here are my unsolved issues as of now:

In trying to install Stage, I was initially getting errors related to libtool, namely:

-- Checking for libtool
CMake Error at libstage/CMakeLists.txt:6 (message):
libtool library not found, aborting

Ubuntu was telling me that I had libtool installed, so I went through the list of software packages and did an apt-get install on all the ones with libtool in the name. This seemed to work for Stage, because it promptly moved on to another error. If I try to make the files according to the instructions, I get:

[ 2%] Building CXX object libstage/CMakeFiles/stage.dir/worldgui.o
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc: In static member function ‘static void Stg::StgWorldGui::fileLoadCb(Fl_Widget*, void*)’:
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc:409: error: ‘class Fl_File_Chooser’ has no member named ‘ok_label’
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc: In member function ‘bool Stg::StgWorldGui::saveAsDialog()’:
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc:600: error: ‘class Fl_File_Chooser’ has no member named ‘ok_label’
make[2]: *** [libstage/CMakeFiles/stage.dir/worldgui.o] Error 1
make[1]: *** [libstage/CMakeFiles/stage.dir/all] Error 2
make: *** [all] Error 2

I've tried installing all the packages for FLTK again, but for whatever reason, it doesn't seem to find this ok_label file. I sent an email out to the Stage support list and went on trying to install Gazebo, which depends on OGRE. After installing more dependencies, I try to make the source and hit this:

 cd . && /bin/bash /home/abouchard/Desktop/ogre/missing --run automake-1.9 --foreign 
OgreMain/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
OgreMain/src/Makefile.am:3: 
OgreMain/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
OgreMain/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
PlugIns/BSPSceneManager/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
PlugIns/BSPSceneManager/src/Makefile.am:3: 
PlugIns/BSPSceneManager/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
PlugIns/BSPSceneManager/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
PlugIns/CgProgramManager/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
PlugIns/CgProgramManager/src/Makefile.am:3: 
PlugIns/CgProgramManager/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
PlugIns/CgProgramManager/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
PlugIns/EXRCodec/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
PlugIns/EXRCodec/src/Makefile.am:3: 
PlugIns/EXRCodec/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
PlugIns/EXRCodec/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
PlugIns/OctreeSceneManager/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
PlugIns/OctreeSceneManager/src/Makefile.am:3: 
PlugIns/OctreeSceneManager/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
PlugIns/OctreeSceneManager/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
PlugIns/ParticleFX/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
PlugIns/ParticleFX/src/Makefile.am:3: 
PlugIns/ParticleFX/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
PlugIns/ParticleFX/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/Direct3D9/src/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
RenderSystems/Direct3D9/src/Makefile.am:6: 
RenderSystems/Direct3D9/src/Makefile.am:6: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/Direct3D9/src/Makefile.am:6: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/GLSL/src/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/GLSL/src/Makefile.am:8: 
RenderSystems/GL/src/GLSL/src/Makefile.am:8: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/GLSL/src/Makefile.am:8: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/GLX/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/GLX/Makefile.am:8: 
RenderSystems/GL/src/GLX/Makefile.am:8: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/GLX/Makefile.am:8: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/Makefile.am:12: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/Makefile.am:12: 
RenderSystems/GL/src/Makefile.am:12: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/Makefile.am:12: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/atifs/src/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/atifs/src/Makefile.am:8: 
RenderSystems/GL/src/atifs/src/Makefile.am:8: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/atifs/src/Makefile.am:8: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/nvparse/Makefile.am:12: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/nvparse/Makefile.am:12: 
RenderSystems/GL/src/nvparse/Makefile.am:12: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/nvparse/Makefile.am:12: to `configure.in' and run `aclocal' and `autoconf' again.
RenderSystems/GL/src/win32/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
RenderSystems/GL/src/win32/Makefile.am:6: 
RenderSystems/GL/src/win32/Makefile.am:6: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
RenderSystems/GL/src/win32/Makefile.am:6: to `configure.in' and run `aclocal' and `autoconf' again.
Samples/Common/CEGUIRenderer/src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
Samples/Common/CEGUIRenderer/src/Makefile.am:3: 
Samples/Common/CEGUIRenderer/src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Samples/Common/CEGUIRenderer/src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
make: *** [Makefile.in] Error 1

Now, I would lying if I tried to pretend that I really understood much of this, but it all seems to be about the libtool library not working correctly, which makes me think that I still haven't fixed the problem I ran into with Stage. Since these issues are across a variety of packages and what seem to be standard packages for Ubuntu, I thought this might be somewhere I could find help. If someone could please give some direction to a lost MechE, I would really appreciate it.

---

