---
title: "CAPT 64bit?"
date: 2010-01-20
forum: Hardware
---

### Post by AmrH on 2010-01-20
I've got a Canon  i-Sensys LBP3010, and I'm running Karmic 64bit. I used to install the 32bit drivers on my old x86 system, now I need the drivers for the 64bit system. Would somebody please help me with that as I've searched a lot, and could find nothing?

---

### Post by AmrH on 2010-01-26
Is there any hope that it'll work?

---

### Post by AmrH on 2010-01-27
Does any body have a tutorial on how to compile the CAPT driver from source? I believe this way will allow me to run the printer on the 64bit system.

---

### Post by tonidito on 2012-11-15
Hi, some days ago I decided to upgrade my Ubuntu 10.04 to the newer   Ubuntu 12.04. Everything went very well, and after some configuration I   felt satisfied. Only a thing created some head scratching: my Canon   printer LBP3010 could not print!
After some unsuccessfully attempts to make the driver functioning I   decided to make some researches in Google. I tried all possible drivers,   deb packages and following strictly all posts that I fount in the   Internet, but... nothing, my printer seems to be dead!
My last chance was to recompile from source. First with unsuccessful   results, due to many error that occurred during the compilation   procedure. Again, after some head scratching and a few sleepless nights   analyzing the source code, I get the right solution and now I have my   LBP3010 fully functioning.

Note that the following procedure is valid for a 64 bit machine.

uname -a gives
Linux toni-laptop 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

In the following I will show the procedure that I followed in order to get the printer working.
First I downloaded the last driver package I found at the Canon web page:

Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz.

Now the procedure to compile.

First step
1) extract the tar.gz package to a folder of Your choice;
2) cd Linux_CAPT_PrinterDriver_V240_uk_EN/Src/
3) untar cndrvcups-capt-2.40-1.tar.gz  and cndrvcups-common-2.40-1.tar.gz
4) cd cndrvcups-common-2.40/
5) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
6) dpkg-buildpackage.

At the end of operation 6) You will find cndrvcups-common_2.40-1_amd64.deb package in Src directory.

7) install it (required for the next compilation steps) with the common 
    sudo dpkg -i cndrvcups-common_2.40-1_amd64.deb

Second step
1) cd cndrvcups-capt-2.40/
2) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
3) gedit debian/rules and uncomment line 172 which will results, then, in 
    #    dh_shlibdeps
    Save and close
4) gedit statusui/src/ppapdata.c and add the header (this is to define variable ppd_size_t)
    #include <cups/ppd.h>
save and close file.
5) gedit cngplp/configure.in and add "AC_CONFIG_MACRO_DIR([m4])" at line 9, save and close
6) gedit cngplp/Makefile.am and add "ACLOCAL_AMFLAGS=-I m4" at line 5, save and close
7) run the following commands in the cngplp directory:
    libtoolize
    aclocal
    automake
cd .. 
9) dpkg-buildpackage

At the end of operation 9) You will find cndrvcups-capt_2.40-1_amd64.deb package in Src directory.

10) install it with 
    sudo dpkg -i cndrvcups-capt_2.40-1_amd64.deb

End of procedure.
From this point You should follow the printer configuration steps as stated in many other posts.

I hope this will help the Ubuntu Community.
Kind regards

---

