---
title: "customized usplash does not work in 8.10"
date: 2008-11-01
forum: General Help
---

### Post by the666pack on 2008-11-01
hello!

version: 8.10 intrepid ibex

i wanted to ask what might be the problem that a customized usplash animation doesnt work. i tried the installation by several tutorials/howtos, but also after going through the mentioned things, i always ended up with the usual init output.

nevertheless i would like to have a nice customized usplash graphic start.

thanks a lot for helping out,

greetings,

mario

---

### Post by Z_o-s-o on 2008-11-02
Same issue as you.

Applying a custom usplash results in a text boot.

---

### Post by kestal on 2008-11-02
confirmed here on my end. rather annoying actually.

---

### Post by ellaguno on 2008-11-02
The same for me.

I uninstalled the Startup Manager, installed new themes but no success.

---

### Post by rfurman24 on 2008-11-02
Same problem here. Very annoying.

---

### Post by utkjamie on 2008-11-05
The upgrade appears to have killed my Ubuntu Peace Usplash screen. I assume no luck with solutions...

---

### Post by the666pack on 2008-11-05
> **utkjamie said:**
> The upgrade appears to have killed my Ubuntu Peace Usplash screen. I assume no luck with solutions...


i personally "solved" the issue with changing to the "splashy" package: here is a short HOWTO for ubuntu version 8.10:

[http://www.bauer-power.net/2008/11/changing-bootup-splash-in-ubuntu-810.html](http://www.bauer-power.net/2008/11/changing-bootup-splash-in-ubuntu-810.html)

you dont find that many customized splashy-themes as for usplash, but the fingerprint theme is quite nice. in addition it is easy to create ones own customized theme in splashy.

cheers and greetings,

mario

---

### Post by morepowerr on 2008-11-05
Ya after getting to to PO at it I did what was probably the wrong thing to do.

 And installed the ones from hardy. With are working just fine.

 libusplash0_0.5.19_i386.deb
 
and 

 usplash_0.5.19_i386.deb


 But now I can't remember how to turn off the update manager looking at them.

--powerr

---

### Post by rfurman24 on 2008-11-06
The downgrade worked for me as well. To lock the version you highlight it in synaptic and then go to package-lock version in the menu.

---

### Post by red_team316 on 2008-11-07
There is nothing wrong with usplash in 8.10 Intrepid. Anyone wanting to use a custom usplash will have to recompile it on an Intrepid box.

There were obviously changes to usplash from Hardy 8.04 to Intrepid 8.10. One of those changes was changing the THEME VERSION to 3. I'm not 100% sure if this is the reason why the old usplashes wont work, but I'm betting on it. A dapper(THEME VERSION 1) usplash doesn't work on Edgy(THEME VERSION 2). It makes sense to me that a hardy(THEME VERSION 2) usplash theme does not work on intrepid(THEME VERSION 3).

[https://launchpad.net/ubuntu/+source/usplash](https://launchpad.net/ubuntu/+source/usplash)

Somebody just needs to update the Usplash Customization page as to what we can do with the new API changes...

---

### Post by AbsentHarvest on 2009-02-23
I also have 8.10
I installed an animated splash theme manually.  Which didn't work.
I couldn't change it back to default, I got the start up manager... Didn't help the situation at all.  I un-installed both components completely.  I have re-installed the usplash... However........ I get a text boot up.
How can I get this back to default?

Also has anyone yet found a way to add customized animated splash themes?)

---

### Post by grndslm on 2009-02-23
The only thing you can do is go into startupmanager and select the ubuntu-default-usplash theme or whatever it is...

I only found 2 other Usplash themes to work on my 8.10 install, chrome-new & linux outside.  I reverted back to 8.04, and now I can't get chrome-new to work...  what a bummer.  Why does Usplash suck so much?  Were we supposed to know that Usplash themes are supposed to be re-compiled yearly??

Splashy's not bad, but the square progress bar is kinda depressing... and it still spits out a little text that at the beginning of a boot that really doesn't belong there.

---

### Post by AbsentHarvest on 2009-02-23
How depressing.
Thanks though. I will try to get it set to default.

---

### Post by red_team316 on 2009-02-26
> **grndslm said:**
> The only thing you can do is go into startupmanager and select the ubuntu-default-usplash theme or whatever it is...

I only found 2 other Usplash themes to work on my 8.10 install, chrome-new & linux outside.  I reverted back to 8.04, and now I can't get chrome-new to work...  what a bummer.  Why does Usplash suck so much?  Were we supposed to know that Usplash themes are supposed to be re-compiled yearly??

Splashy's not bad, but the square progress bar is kinda depressing... and it still spits out a little text that at the beginning of a boot that really doesn't belong there.

Sorry, but thats just the way usplash was created. In fact, it's not uncommon for any software/program for that matter to break binary compatibility between versions.

The real solution to your problem is to get the users who make usplashes to create a deb that builds it from the source as it is installing, that way regardless of what version you are running, most likely it will work. 

If the source is provided, it's as easy as having libusplash-dev, libbogl-dev, build-essential, libc6-dev, gcc installed and then going into the source directory and typing "make".

My parallax usplash(link in my sig) has binaries for x86 and x64 for both intrepid and hardy as well as the source code. Hopefully you or others will get some use out of it as of current usplash is doomed to be replaced by plymouth(which is superior to both usplash and splashy) when Ubuntu 9.10 arrives.

---

### Post by grndslm on 2009-02-26
> **red_team316 said:**
> **The real solution to your problem is** to get the users who make usplashes to create a deb that builds it from the source as it is installing, that way regardless of what version you are running, most likely it will work.

...

Hopefully you or others will get some use out of it as of current usplash is doomed to be replaced by plymouth(which is superior to both usplash and splashy) when Ubuntu 9.10 arrives.No...  A real solution to our problem is to wait 8 more months and not even mess with Usplash.  I'm not going to convince any creator of Usplash themes of anything but to start creating Plymouth themes.

---

### Post by red_team316 on 2009-02-27
true, true. I'm anxiously awaiting the Plymouth PPA for Jaunty so I can start making some plugins. I really dont see plymouth getting knocked off so easily. Although at this point in time, thats not an viable option :(

I have to say that the solution above is a viable idea. If ubuntu applied this concept to all of their packages, they could cut their repositories in half as long as the base system includes the proper build tools. Since that creates a longer install time, I don't really see it happening until computers ship with 200-core procs and 256TB of RAM so that it is transparent to non-developers :P

---

### Post by minotauros on 2009-03-01
Hello, I am new in all this, but maybe this is helpful (?)

I will use ubuntu reflections alternative usplash [http://www.gnome-look.org/content/sh...ontent=92519](http://www.gnome-look.org/content/sh...ontent=92519) as an example.

First go to where the usplash theme was downloaded and tar -xf *.tar.gz and then cd to the directory. You then have to make and make install the theme because it was originally made for 8.04

Henceforth:

$ make
$ sudo make install
$ sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu.so 10
$ sudo update-initramfs -u

This last line is important... If you do not use it, you will get your new theme only at log-out and not at log-in.

Of course in this example the Ubuntu-Reflections produces and links an usplash-theme-ubuntu.so and not an ubuntu-reflections-theme.so

If you are using a theme that produces a uplash different *.so you should direct it there... So assuming the above ubuntu-reflections-theme.so:

$ sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/ubuntu-reflections-theme.so 10

---

