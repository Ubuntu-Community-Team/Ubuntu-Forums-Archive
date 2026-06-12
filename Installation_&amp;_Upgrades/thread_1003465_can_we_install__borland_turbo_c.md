---
title: "can we install  borland turbo c?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by abhilashm86 on 2008-12-06
can we install turbo c because i want to to use graphics directory,i don't know whether its present int linux???

---

### Post by cb951303 on 2008-12-06
I don't understand what is a graphics directory but if you want a graphics.h compatible library here it is: [http://savannah.nongnu.org/projects/libgraph/](http://savannah.nongnu.org/projects/libgraph/)

it should be in synaptic.

---

### Post by abhilashm86 on 2008-12-06
hey graphics option is used to draw graphs based on outputs,so i was thinking to do in linux ...........

---

### Post by snova on 2008-12-06
Is there any particular reason you need Borland C? If you just need a compiler, use GCC.

---

### Post by abhilashm86 on 2008-12-07
ya snova i use GCC compiler,but to work using graphics i need turbo c,so thought can i install it,wil gcc compiler support graphics,do u have any idea??

---

### Post by abhilashm86 on 2008-12-07
> **snova said:**
> Is there any particular reason you need Borland C? If you just need a compiler, use GCC.

i also like the tracing option(F7) using turbo c,also for my projects of image processing i need to draw graphs,so i asked about installing turbo c in linux......

---

### Post by cb951303 on 2008-12-07
> **abhilashm86 said:**
> ya snova i use GCC compiler,but to work using graphics i need turbo c,so thought can i install it,wil gcc compiler support graphics,do u have any idea??

what is this graphics support you're talking about?

---

### Post by abhilashm86 on 2008-12-07
> **cb951303 said:**
> what is this graphics support you're talking about?

the graphics is about plotting graph in 2-dimensional plane using<graphics.h> library based on input and output parameters,we usually use initgraph to construct and build the graph,can we do this application in linux?

---

### Post by cb951303 on 2008-12-07
> **abhilashm86 said:**
> the graphics is about plotting graph in 2-dimensional plane using<graphics.h> library based on input and output parameters,we usually use initgraph to construct and build the graph,can we do this application in linux?

so what's wrong with the library that I recommended you? libgraph for GCC is fully compatible with graphics.h. look at my first post in this topic for link. from their site:

> 
libgraph is an implementation of the TurboC graphics API (graphics.h) on GNU/Linux using SDL. The library requires SDL for primitive graphics and SDL_image (to blit fonts). Functions for text display are based heavily on code "borrowed" from Karl Bartel's SFont library.

---

### Post by beyboo on 2008-12-07
Let me add some clarity here.

Abhilash, the Turbo C / C++ compiler you are mentioning is an 1988 legacy product which was aimed at MS-Dos compatabile x86, 286, 386 based machines. The BGI Library was based on so-called graphics calls to draw pixels in a graphic mode. MS Dos executables which used this BGI library switched the monitor mode in to VGA, SVGA mode and allowed pixels to be drawn. To take it further inbuilt functions like line, circle, rectangle and fill helped to make basic shapes. 

I remember learning my concepts using Windows 3.1, MS - Dos way back in the 1990's. 

Windows could run it as it has backward compatibility to Dos programs. Let me also mention here, that the program were run in a simulated mode. 

This technology is old, good to learn concepts, but will require you to install MS Dos Simulators (Like Wine is a windows emulator). 

You need to now take on the new technology under Linux. There is NO BGI library as you mention. However you may run any old Dos program (yes including Turbo C) using DosBox. You will find it in the repositories. 

While you are at it, you will also be able to run Doom for Dos, Duke 3D, Wolf 3d and all those Dos games from way back then !! ):P

---

### Post by abhilashm86 on 2008-12-07
> **cb951303 said:**
> so what's wrong with the library that I recommended you? libgraph for GCC is fully compatible with graphics.h. look at my first post in this topic for link. from their site:

hey i downloaded the libraries which u said and installed,i even found at synaptic package manager,but my compiler throwed error saying initgraph is not defined!!!!!!anyways i am trying searching in net,could u give me some internet links which provides programming under linux, because these many days i used windows and turbo, so its slight difficult to adjust..........
thanks to forums coz they helped me a lot wid my doubts!!!!:p

---

### Post by abhilashm86 on 2008-12-07
> **beyboo said:**
> Let me add some clarity here.

Abhilash, the Turbo C / C++ compiler you are mentioning is an 1988 legacy product which was aimed at MS-Dos compatabile x86, 286, 386 based machines. The BGI Library was based on so-called graphics calls to draw pixels in a graphic mode. MS Dos executables which used this BGI library switched the monitor mode in to VGA, SVGA mode and allowed pixels to be drawn. To take it further inbuilt functions like line, circle, rectangle and fill helped to make basic shapes. 

I remember learning my concepts using Windows 3.1, MS - Dos way back in the 1990's. 

Windows could run it as it has backward compatibility to Dos programs. Let me also mention here, that the program were run in a simulated mode. 

This technology is old, good to learn concepts, but will require you to install MS Dos Simulators (Like Wine is a windows emulator). 

You need to now take on the new technology under Linux. There is NO BGI library as you mention. However you may run any old Dos program (yes including Turbo C) using DosBox. You will find it in the repositories. 

While you are at it, you will also be able to run Doom for Dos, Duke 3D, Wolf 3d and all those Dos games from way back then !! ):P

currently i am using wine,how to install MS dos simulator and dosbox, can u brief me on that concepts please,are there any other options to use graphics library:p

---

### Post by beyboo on 2008-12-07
> **abhilashm86 said:**
> hey i downloaded the libraries which u said and installed,i even found at synaptic package manager,but my compiler throwed error saying initgraph is not defined!!!!!!anyways i am trying searching in net,could u give me some internet links which provides programming under linux, because these many days i used windows and turbo, so its slight difficult to adjust..........
thanks to forums coz they helped me a lot wid my doubts!!!!:p

Abhi you need to understand that each lib for doing any task has its own call procedure. The initigraph() function of turbo c/c++ was for invoking its graphics library. The new lib will have its own and u will have its own code. C / C++ is indeed portable but only the default set, not the 3rd party libs. 

You would do well with this murphy's law


When all else fails, reads the manuals !!

---

### Post by beyboo on 2008-12-07
> **abhilashm86 said:**
> currently i am using wine,how to install MS dos simulator and dosbox, can u brief me on that concepts please,are there any other options to use graphics library:p

Wine is a windows emulator and not connected to Dos programs. 

Like Wine, Dosbox is a DOS emulator. It will run all ur old MS Dos programs including the Borland Turbo C IDE program. However it is possible that a few  programs you compile under the IDE may not run, if u r using direct memory access algorithms which are not supported. 

Once you install Dosbox, you will get a familiar Dos prompt
Refer to the manual here [http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox](http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox)

Install Turbo  C, your IDE will run "natively" in Dos mode.

---

### Post by abhilashm86 on 2008-12-07
> **beyboo said:**
> Wine is a windows emulator and not connected to Dos programs. 

Like Wine, Dosbox is a DOS emulator. It will run all ur old MS Dos programs including the Borland Turbo C IDE program. However it is possible that a few  programs you compile under the IDE may not run, if u r using direct memory access algorithms which are not supported. 

Once you install Dosbox, you will get a familiar Dos prompt
Refer to the manual here [http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox](http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox)

Install Turbo  C, your IDE will run "natively" in Dos mode.

ok thanks lot beyboo,i am downloading dosbox,i'll reply after trying it..........

---

### Post by abhilashm86 on 2008-12-07
> **beyboo said:**
> Wine is a windows emulator and not connected to Dos programs. 

Like Wine, Dosbox is a DOS emulator. It will run all ur old MS Dos programs including the Borland Turbo C IDE program. However it is possible that a few  programs you compile under the IDE may not run, if u r using direct memory access algorithms which are not supported. 

Once you install Dosbox, you will get a familiar Dos prompt
Refer to the manual here [http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox](http://www.dosbox.com/wiki/Basic_Setup_and_Installation_of_DosBox)

Install Turbo  C, your IDE will run "natively" in Dos mode.

beyboo please tell me now how to install turbo c,i have done installation with dosbox............

---

### Post by beyboo on 2008-12-07
> **abhilashm86 said:**
> beyboo please tell me now how to install turbo c,i have done installation with dosbox............

copy the TC or Turboc directory what you normally use in your home folder in ubuntu.

Start Dosbox emulator from Applications > Games menu

once at the Z: prompt, type mount c ~/tc <enter>

Be sure to replace tc with the exact name, case matters.

Thats it, change to C: prompt and start using your turboc !!

Edit : If you dont have Turbo C. download from here [http://dn.codegear.com/article/20841](http://dn.codegear.com/article/20841)

I still think this is antique, please update your knowledge and use the latest libraries which are current and native with linux

---

### Post by ashwin.kj on 2009-01-06
> **abhilashm86 said:**
> beyboo please tell me now how to install turbo c,i have done installation with dosbox............

U can find the step by step procedure at [http://dogbuntu.wordpress.com/2007/0...-ubuntu-linux/](http://dogbuntu.wordpress.com/2007/0...-ubuntu-linux/)

---

