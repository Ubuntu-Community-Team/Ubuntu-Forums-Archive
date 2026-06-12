---
title: "General Lagginess with Alps Touchpad"
date: 2009-09-16
forum: Hardware
---

### Post by ElTimo on 2009-09-16
I've had this problem since time immemorial, and I've yet to find a fix for it. Movement on Alps GlidePoint Touchpad lags by about 1/20th of a second or so, and tapping takes a good quarter of a second before it's recognized as a click. Luckily, I have a TrackPoint (nipple mouse, for those less proper among us), but it has a tendency to start drifting randomly. I've heard rumblings about a Linux driver for Alps pads, but have yet to find anything about it. Can someone please advise? I'm getting sick of using the stick mouse, and my touchpad is too slow to be enjoyable.

---

### Post by myandylai on 2009-10-11
Recently I purchase a HP CQ40 series laptop with ALPS Touchpad unlucky. I am having the same problem. Is anyone out there know how to configure it correctly kindly reply. Thanks for the help.

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

### Post by sumi76 on 2009-11-03
Hi Folks!

I had exactly the same problem after upgrading from Jaunty to Karmic.
I have an Acer TravelMate 290 series with ALPS Touchpad. Drove me crazy...
After a good deal of time I've found a configuration ***[guide]("http://www.bhagwad.com/blog/2009/technology/configure-alps-synaptics-touchpad-in-ubuntu-904-jaunty-jackalope.html")*** where a certain
GPointing Device Settings was mentioned.
It seems, that at the time there was no GUI available, but I checked it in
the Synaptic Package Manager and found this package: **gpointing-device-settings**
Installed, and ran it via Alt+F2 (couldn't figure out where it is...).
Set Touchpad on in the General tab and_ checked Enable faster tapping_ on the Tapping tab.
That made the trick, my touchpad works as usual.

Hope it helps!

Another option without installing anything:

synclient manages the touchpad in my case (my xorg.conf doesn't contain an input.device section),
so open terminal window and type [COLOR=Red]synclient -l
[/COLOR]It lists the settings for the touchpad. Search for FastTaps. If it's 0, change it to 1 by typing
[COLOR=Red]synclient FastTaps=1[/COLOR]

I agree with the author of the config guide I mentioned above, there should be a GUI for detailed touchpad settings.
Of course one can play with the command line if there's enough time for it...

Good day for all!

---

### Post by sumi76 on 2009-11-05
Meanwhile it turned out, that the value for FastTaps changes back to 0 after reboot.
So I went back to the first option (installed **gpointing-device-settings**), and now the
value for FastTaps stays 1 after restart.

There's one more thing I observed. When I first installed the gpointing GUI the settings I made there were altered after closing the window and opening it again (even though the Enable faster tapping still worked). The touchpad was set to OFF whereas it was up and running. After removing gpointing and disabling "touchpad while typing" option in the System > Preferences > Mouse > Touchpad tab I reinstalled the GUI again and since than it is working like a charm.

It would be useful to know why the settings made in command line are changed back to
default after reboot (there are 2 I know of: TouchpadOff and FastTaps).

Any ideas?

---

### Post by ElTimo on 2010-01-12
I know this thread is dead, but I tried to compile the ALPS driver on Karmic 64 bit and I got the following error:```
tim@Cygnus-X1:~/Downloads/alps-2009-10-16-1706$ make
make  all-recursive
make[1]: Entering directory `/home/tim/Downloads/alps-2009-10-16-1706'
Making all in src
make[2]: Entering directory `/home/tim/Downloads/alps-2009-10-16-1706/src'
  CXX    Alps.lo
Alps.cc: In member function ‘void Alps::readInput()’:
Alps.cc:481: error: invalid conversion from ‘long unsigned int (*)(_OsTimerRec*, long unsigned int, void*)’ to ‘CARD32 (*)(_OsTimerRec*, CARD32, void*)’
Alps.cc:481: error:   initializing argument 4 of ‘_OsTimerRec* TimerSet(_OsTimerRec*, int, CARD32, CARD32 (*)(_OsTimerRec*, CARD32, void*), void*)’
make[2]: *** [Alps.lo] Error 1
make[2]: Leaving directory `/home/tim/Downloads/alps-2009-10-16-1706/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tim/Downloads/alps-2009-10-16-1706'
make: *** [all] Error 2
```
Does the CARD32 have anything to do with the OS being 32 bit? If so, is there any way to fix it?

---

### Post by marcopl on 2010-03-19
bro, this thread is not dead !!!! i have been using karmic for quite sometime now but uptill now, i cant get my alps touchpad to work !!!!!! AAAAHHHHHHH  

i have a hp compaq cq40 laptop. Did u ever solve yr problem? 

> **ElTimo said:**
> I know this thread is dead, but I tried to compile the ALPS driver on Karmic 64 bit and I got the following error:```
tim@Cygnus-X1:~/Downloads/alps-2009-10-16-1706$ make
make  all-recursive
make[1]: Entering directory `/home/tim/Downloads/alps-2009-10-16-1706'
Making all in src
make[2]: Entering directory `/home/tim/Downloads/alps-2009-10-16-1706/src'
  CXX    Alps.lo
Alps.cc: In member function ‘void Alps::readInput()’:
Alps.cc:481: error: invalid conversion from ‘long unsigned int (*)(_OsTimerRec*, long unsigned int, void*)’ to ‘CARD32 (*)(_OsTimerRec*, CARD32, void*)’
Alps.cc:481: error:   initializing argument 4 of ‘_OsTimerRec* TimerSet(_OsTimerRec*, int, CARD32, CARD32 (*)(_OsTimerRec*, CARD32, void*), void*)’
make[2]: *** [Alps.lo] Error 1
make[2]: Leaving directory `/home/tim/Downloads/alps-2009-10-16-1706/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tim/Downloads/alps-2009-10-16-1706'
make: *** [all] Error 2
```
Does the CARD32 have anything to do with the OS being 32 bit? If so, is there any way to fix it?

---

