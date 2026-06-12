---
title: "[SOLVED] Installing Tux: a Quest for Herring"
date: 2008-10-15
forum: General Help
---

### Post by bwang on 2008-10-15
I can't get Tux: a Quest for Herring to compile. Here is the output of ./configure:
```
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for windows.h... no
checking for X... libraries , headers 
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for glNewList in -lGL... yes
checking for gluLookAt in -lGLU... yes
checking for glutGetModifiers in -lglut... yes
checking for ALopenport in -laudio... no
checking for ANSI C header files... yes
checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glut.h... yes
checking for windows.h... (cached) no
checking for joystick.h... no
checking for linux/joystick.h... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating contrib/Makefile
creating data/Makefile
creating doc/Makefile
creating fonts/Makefile
creating images/Makefile
creating models/Makefile
creating mods/Makefile
creating penguin/Makefile
creating slamcode/Makefile
creating src/Makefile
creating wavs/Makefile

```

and here is the output of make:
```
Making all in src
make[1]: Entering directory `/home/bayley/tux_aqfh-1.0.14/src'
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c camera.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c components.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c fade_out.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c feature.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c gfx.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c globalstate.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c gui.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c hooks.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c score.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c isect.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c level.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c material.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c ocean.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c orca.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c penguin.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c rocket.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c sound.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c starwing.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
starwing.cxx: In member function ‘void StarWing::strategy(float*)’:
starwing.cxx:127: warning: ‘nearest[0]’ may be used uninitialized in this function
starwing.cxx:127: warning: ‘nearest[1]’ may be used uninitialized in this function
starwing.cxx:127: warning: ‘nearest[2]’ may be used uninitialized in this function
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c status.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c surf_rev.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c tux.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c tuxstate.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c whale.cxx
level.h:35: warning: ‘class ActiveThingInstance’ has virtual functions but non-virtual destructor
level.h:70: warning: ‘class SnowballInstance’ has virtual functions but non-virtual destructor
level.h:94: warning: ‘class SmokePuffInstance’ has virtual functions but non-virtual destructor
level.h:112: warning: ‘class BubbleInstance’ has virtual functions but non-virtual destructor
level.h:130: warning: ‘class RingInstance’ has virtual functions but non-virtual destructor
level.h:137: warning: ‘class TuxLifeInstance’ has virtual functions but non-virtual destructor
level.h:145: warning: ‘class HerringInstance’ has virtual functions but non-virtual destructor
level.h:157: warning: ‘class MessageInstance’ has virtual functions but non-virtual destructor
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamRun.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamCodeGen.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamExpression.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slam.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamStatement.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamSymbols.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGL=1 -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/local/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamToken.cxx
c++  -g -O2 -O6 -Wall  -o tux_aqfh  camera.o components.o fade_out.o feature.o gfx.o globalstate.o gui.o hooks.o score.o isect.o level.o material.o ocean.o orca.o penguin.o rocket.o sound.o starwing.o status.o surf_rev.o tux.o tuxstate.o whale.o slamRun.o slamCodeGen.o slamExpression.o slam.o slamStatement.o slamSymbols.o slamToken.o  -lplibsl -lplibssg -lplibpu -lplibfnt -lplibsg -lplibul -lglut -lGLU -lGL    -lSM -lICE -lpthread -lX11 -lXi -lXext -lXmu  -lm
gui.o: In function `GUI::joystickInput()':
/home/bayley/tux_aqfh-1.0.14/src/gui.cxx:276: undefined reference to `jsJoystick::read(int*, float*)'
gui.o: In function `GUI':
/home/bayley/tux_aqfh-1.0.14/src/gui.cxx:172: undefined reference to `jsJoystick::jsJoystick(int)'
/home/bayley/tux_aqfh-1.0.14/src/gui.cxx:172: undefined reference to `jsJoystick::jsJoystick(int)'
collect2: ld returned 1 exit status
make[1]: *** [tux_aqfh] Error 1
make[1]: Leaving directory `/home/bayley/tux_aqfh-1.0.14/src'
make: *** [all-recursive] Error 1

```

Has anyone gotten this to compile? I'm running Ubuntu 7.10 and I have the plib and opengl development files installed.

---

### Post by fsmithred on 2008-10-16
```
sudo apt-get install planetpenguin-racer
```

---

### Post by Yellow Pasque on 2008-10-17
Look like jsjoystick is part of plib:
```
sudo apt-get install plib1.8.4-dev
```

---

### Post by bwang on 2008-10-17
I already have plib1.8.4-dev installed.

---

### Post by bwang on 2008-10-19
Has anyone gotten this game to work?

---

### Post by bwang on 2009-01-04
Woohoo! I got it to work, using [this page.]("https://www.linuxquestions.org/questions/linux-games-33/cant-install-tux-a-quest-for-herring.-cry-sob-make-problems...-229483/"). If you want to get it to work, open configure in a text editor, and change line 1362 to:
```
plib_suffix="-lplibsl -lplibssg -lplibpu -lplibfnt -lplibsg -lplibul -lplibjs"
```

---

