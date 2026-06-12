---
title: "kinect problem when running touchd &quot;No IIDC camera with requested index found.&quot;"
date: 2010-11-24
forum: Hardware
---

### Post by motorbuntu on 2010-11-24
Ubuntu 10.10 x86
Asus 1215n

trying to get kinect going on my laptop I followed the instructions posted here: 

[http://www.omgubuntu.co.uk/2010/11/multi-touch-in-ubuntu-using-kinect-video-ppa/](http://www.omgubuntu.co.uk/2010/11/multi-touch-in-ubuntu-using-kinect-video-ppa/) 
[INDENT] **sudo apt-add-repository ppa:floe/libtisch**
 **sudo apt-get update && sudo apt-get install libtisch libtisch-dev libtisch-csharp libtisch-java libtisch-python**
 [/INDENT]cos@cos1215:~$ touchd -v
touchd - libTISCH 1.1 image processing layer
(c) 2008 by Florian Echtler <echtler@in.tum.de>
Caught runtime exception:
  No IIDC camera with requested index found.
Cleaning up.. done. Goodbye.

It appears my built in webcam may have the index touchd is assuming to be the kinect,  but I have no idea where to get the indexes or if there is a config file to fix it. any help would be greatly appreciated. 

Thanks.

---

### Post by Andros1975 on 2010-11-24
hi man, did you get this to work?  i have the same issue

---

### Post by airydragon on 2010-11-27
take a look at [http://sourceforge.net/tracker/?func=detail&aid=3112733&group_id=232685&atid=1087605](http://sourceforge.net/tracker/?func=detail&aid=3112733&group_id=232685&atid=1087605)

---

### Post by stevenmansour on 2010-11-30
Same problem here. Kinect works fine with glview application, but I can't figure out how to get past "No IIDC camera with requested index found."

I've already tried unplugging all other USB devices as mentioned in other comment threads. 

Anyone else have any luck?

---

### Post by stevenmansour on 2010-12-02
I've also tried compiling from source using the instructions found [here]("http://hackaday.com/2010/11/13/kinect-and-tisch-combined-for-multitouch/"), but the syntax is a bit off - I can get glview to work with the compiled version of libkinect, but can't seem to get the right flags / settings / config to compile libtisch. 

Any help appreciated!

---

### Post by cyberey66 on 2010-12-04
So what can we do with the kinect over a webcam?  I'm actually curious, it might be worth buying one if I can write software for it. 

 I hacked together some software, using a webcam as input, that allows me to move around my desktop cube by 'grabbing' it with my hand.  It's useless in the practical sense, but that’s not the point.

[http://www.youtube.com/watch?v=EOEP8ZKQ9GM](http://www.youtube.com/watch?v=EOEP8ZKQ9GM)

---

### Post by floem on 2010-12-06
> **stevenmansour said:**
> I've also tried compiling from source using the instructions found [here]("http://hackaday.com/2010/11/13/kinect-and-tisch-combined-for-multitouch/"), but the syntax is a bit off - I can get glview to work with the compiled version of libkinect, but can't seem to get the right flags / settings / config to compile libtisch.
Hi, I've just been pointed to this thread and I'll try to clear some things from those instructions up.

- The Ubuntu packages from the PPA don't support Kinect at the moment, as there's no PPA for libfreenect yet - so you have to compile libtisch from source.
- The libfreenect repository is now at [https://github.com/OpenKinect/libfreenect](https://github.com/OpenKinect/libfreenect)
- You don't need to edit any CMakeLists anymore, just run "cmake . && make".
- The includes and libs are now directly in libfreenect/include and libfreenect/lib.
- Therefore, the commandline to compile libtisch looks something like this now:
CFLAGS=-I/foobar/libfreenect/include LDFLAGS="-L/foobar/libfreenect/lib -lfreenect" make install
(Obviously, you have to adapt /foobar to match your own directory structure.)

After that, the rest of the instructions (particularly those relating to the $HOME/.tisch.touchd config file, still apply.

Hope this helps!
Florian

---

### Post by AlwaysLearning on 2010-12-29
A quick walkthrough for those still having problems...

Note that since you're building from source code you'll need the dev versions of freeglut and libusb:
```
sudo apt-get install cmake gitg freeglut3-dev libusb-1.0-0-dev
```

Now, in the directory you want to clone the libfreenect source code to, eg: ~/Projects

```
git clone git://github.com/OpenKinect/libfreenect.git
cd libfreenect
cmake .
make
```

At this point you should be able to test that libfreenect is correctly compiled by doing this:
```
cd ~/Projects/libfreenect/lib
../bin/glview
```

If you get this error:
```
libusb couldn't open USB device /dev/bus/usb/001/006: Permission denied.
libusb requires write access to USB device nodes.
```

Try this instead (use the device path from the above error message, note that it might change if you unplug/replug the Kinect):
```
sudo chmod a+rw /dev/bus/usb/001/006
sudo chmod a+rw /dev/bus/usb/001/008
../bin/glview
```

If successful you should see a window appear with the live 3D depth map on the left and live video on the right. Use the w/s/x keys to tilt the camera up and down and the keys 0-6 to change the LED colour/blink.

Once you've gotten to this point you should be able to install the drivers.

Good luck.

---

### Post by Nathanv.1 on 2011-01-04
Thank you last person but I cant seem to get the code ```
make .
``` to work.

I get this ```
nathan@nathan-laptop:~/libfreenect$ cmake .
-- Operating system is Linux
-- Got System Processor i686
-- libfreenect will be installed to /usr/local
-- Headers will be installed to /usr/local/include/libfreenect
-- Libraries will be installed to /usr/local/lib
-- Found libusb-1.0:
--  - Includes: /usr/include
--  - Libraries: /usr/lib/libusb-1.0.so
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
GLUT_Xi_LIBRARY (ADVANCED)
    linked by target "cppview" in directory /home/nathan/libfreenect/examples
    linked by target "glpclview" in directory /home/nathan/libfreenect/examples
    linked by target "glview" in directory /home/nathan/libfreenect/examples
GLUT_Xmu_LIBRARY (ADVANCED)
    linked by target "cppview" in directory /home/nathan/libfreenect/examples
    linked by target "glpclview" in directory /home/nathan/libfreenect/examples
    linked by target "glview" in directory /home/nathan/libfreenect/examples

-- Configuring incomplete, errors occurred!

```

any help will be appreciated.

Also, I know this may sound pretty newbish of me but can someone just all the coding needed in the order needed to make this work?

---

### Post by floem on 2011-01-05
Hello nathanv,

you can try the following before running cmake:
```

sudo apt-get install libxmu-dev libxi-dev 

```

Floe

---

### Post by Nathanv.1 on 2011-01-05
Thank you floe, but I still couldnt get it to work and because I had been trying so much stuff that there were copies of stuff all over the hard drive I just reinstalled Ubuntu. I may have doomed myself but it would be nice if someone could point me towards or tell me step by step newbie directions on how to get this to work.

Thank You

---

### Post by kat_ams on 2011-07-23
There is a ppa available for libfreenect

[http://openkinect.org/wiki/Getting_Started#Ubuntu](http://openkinect.org/wiki/Getting_Started#Ubuntu)

It works pretty much out of the box with Ubuntu Lucid. It does not work with Natty.

I was then able to get simple mouse movements by compiling

[https://github.com/Ooblik/Kinect-Mouse/](https://github.com/Ooblik/Kinect-Mouse/)

touchd I still have not been able to get working. Will try to recompile libTISCH by hand see if it can find libfreenect now.

Also according to the wiki for touchd you need to change the camera type from 2 (firewire IIDC) to 5 (kinect)

[https://sourceforge.net/apps/mediawiki/tisch/index.php?title=Touchd_config](https://sourceforge.net/apps/mediawiki/tisch/index.php?title=Touchd_config)

so in the file ~./tisch.touchd you have to change the lines that look like this

752 480 0 **2** 127 8 255 0

to this

640 480 30 **5** 127 8 255 0

---

### Post by kat_ams on 2011-07-23
Now I'm stuck. libtisch will not make.

I build libfreenect by hand as instructed then did a make as such 
kat@linus:**~/libtisch-1.1$ CFLAGS=-I/home/kat/libfreenect/include LDFLAGS="-L/home/kat/libfreenect/lib -lfreenect" make install**

The result of the failed make.

```

make COMMAND=install all
make[1]: Map '/home/kat/libtisch-1.1' wordt binnengegaan
make -C libs/tools install
make[2]: Map '/home/kat/libtisch-1.1/libs/tools' wordt binnengegaan
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing  -I. Socket.cc -o Socket.o
Socket.cc: In member function &#8216;virtual int SocketStream::underflow()&#8217;:
Socket.cc:262: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result
Socket.cc: In member function &#8216;void SocketStream::put_char(int)&#8217;:
Socket.cc:292: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result
Socket.cc: In member function &#8216;void SocketStream::put_buffer()&#8217;:
Socket.cc:299: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing  -I. BasicBlob.cc -o BasicBlob.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing  -I. Thread.cc -o Thread.o
g++ -Wall -ggdb -fPIC -L/home/kat/libtisch-1.1/build//lib/ -shared -Wl,-soname,libtools.so.1 -L/home/kat/libfreenect/lib -lfreenect -Wall -ggdb -L/home/kat/libtisch-1.1/build//lib/ -ldc1394    -lGL -lGLU -lglut -lpthread  Socket.o BasicBlob.o Thread.o -o libtools.so.1.1
ln -s libtools.so.1.1 libtools.so.1
ln -s libtools.so.1 libtools.so
mkdir -p /home/kat/libtisch-1.1/build//bin/
mkdir -p /home/kat/libtisch-1.1/build//lib/
mkdir -p /home/kat/libtisch-1.1/build//include/libtisch/
mkdir -p /home/kat/libtisch-1.1/build//share/doc/libtisch/
mkdir -p /home/kat/libtisch-1.1/build//share/libtisch/
ldid -S  libtools.so.1.1
make[2]: ldid: Command not found
make[2]: [install] Fout 127 (genegeerd)
cp  /home/kat/libtisch-1.1/build//bin/
cp: missing destination after &#8216;/home/kat/libtisch-1.1/build//bin/&#8217;
Typ 'cp --help' voor meer informatie.
make[2]: [install] Fout 1 (genegeerd)
cp  /home/kat/libtisch-1.1/build//share/libtisch/
cp: missing destination after &#8216;/home/kat/libtisch-1.1/build//share/libtisch/&#8217;
Typ 'cp --help' voor meer informatie.
make[2]: [install] Fout 1 (genegeerd)
cp libtools.so.1.1 /home/kat/libtisch-1.1/build//lib/
cp  /home/kat/libtisch-1.1/build//lib/
cp: missing destination after &#8216;/home/kat/libtisch-1.1/build//lib/&#8217;
Typ 'cp --help' voor meer informatie.
make[2]: [install] Fout 1 (genegeerd)
cp -a *.so* /home/kat/libtisch-1.1/build//lib/
cp *.h ../..//tisch.h /home/kat/libtisch-1.1/build//include/libtisch/
cp ../..//README ../..//scripts/tisch.sh ../..//scripts/calib.sh /home/kat/libtisch-1.1/build//share/doc/libtisch/
make[2]: Map '/home/kat/libtisch-1.1/libs/tools' wordt verlaten
make -C libs/simplecv install
make[2]: Map '/home/kat/libtisch-1.1/libs/simplecv' wordt binnengegaan
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ IntensityImage.cc -o IntensityImage.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ RGBImage.cc -o RGBImage.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ YUV420Image.cc -o YUV420Image.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ YUV420SPImage.cc -o YUV420SPImage.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ YUYVImage.cc -o YUYVImage.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ Line.cc -o Line.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ Circle.cc -o Circle.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ ShortImage.cc -o ShortImage.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ ColorLUT.cc -o ColorLUT.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ DCImageSource.cc -o DCImageSource.o
g++ -c -I/home/kat/libfreenect/include -Wall -ggdb -fPIC -DTISCH_SHARED="" -DTIXML_USE_STL -I. -DTISCH_PREFIX='"/home/kat/libtisch-1.1/build//share/libtisch/"' -DHAS_DC1394 -DHAS_FREENECT -O2 -fno-strict-aliasing -I../..//libs/tools/ -I../..//calibd/ KinectImageSource.cc -o KinectImageSource.o
KinectImageSource.cc: In function &#8216;void depth_cb(freenect_device*, void*, uint32_t)&#8217;:
KinectImageSource.cc:64: error: &#8216;FREENECT_DEPTH_11BIT_SIZE&#8217; was not declared in this scope
KinectImageSource.cc: In function &#8216;void rgb_cb(freenect_device*, void*, uint32_t)&#8217;:
KinectImageSource.cc:71: error: &#8216;FREENECT_VIDEO_RGB_SIZE&#8217; was not declared in this scope
KinectImageSource.cc: In function &#8216;void* kinecthandler(void*)&#8217;:
KinectImageSource.cc:82: error: &#8216;freenect_set_video_format&#8217; was not declared in this scope
make[2]: *** [KinectImageSource.o] Fout 1
make[2]: Map '/home/kat/libtisch-1.1/libs/simplecv' wordt verlaten
make[1]: *** [libs/simplecv] Fout 2
make[1]: Map '/home/kat/libtisch-1.1' wordt verlaten
make: *** [install] Fout 2
kat@linus:~/libtisch-1.1$ 


```

I translated the Dutch error messages back to English for this thread.

Any ideas as to why this is failing?

---

### Post by randomjoh on 2012-01-26
Here's my conundrum: glview is working just fine, but cheese, flash, etc say that there's no camera connected.

---

