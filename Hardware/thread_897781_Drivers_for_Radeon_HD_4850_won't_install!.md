---
title: "Drivers for Radeon HD 4850 won't install!"
date: 2008-08-22
forum: Hardware
---

### Post by [compactwelve] on 2008-08-22
Hello there. I am dual booting the 32 bit version of 8.04LTS with Windows Vista 32 bit as the first partition on an HP Pavillion. In this pavillion, there is a Radeon HD 4850 graphics card which I installed, got working under vista, and hoped to get working under linux. I downloaded the drivers from amd's website and every time i try to click the .run file, I get this error message from Gedit:
[img]http://img133.imageshack.us/img133/1081/gediterrorek7.jpg[/img]
I downloaded the English version [since it's the only one available for linux]. Do i need to download a character pack? If so, which one? Or am I just doing this completely wrong? Help! XC

---

### Post by CrossEyedJedi on 2008-09-14
I just installed an ATI 3850 in my Ubuntu rig using Envy, you can download [Envy here]("http://albertomilone.com/nvidia_scripts1.html").  I hope this helps.

---

### Post by markbuntu on 2008-09-14
For the 4850, you need to follow this guide here, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Gui](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Gui)

---

### Post by fwaokda on 2009-07-11
method 2 there seems to no longer work... unless I'm missing something here.  Can someone please help me install the 4850 :( ???

---

### Post by Vakman on 2009-07-11
Open up a terminal. Next type:
```
sudo sh "fileyouwanttoinstall.run"
```
So open terminal and type "sudo sh" and then to make it easier on yourself to find the location, just drag the file into the terminal and it will insert the location of the file. Press enter, enter password if asked. Then this will start the install. You can't simply click on .run files. Hope this helps.

---

### Post by fwaokda on 2009-07-11
> **Thisislaw said:**
> Open up a terminal. Next type:
```
sudo sh "fileyouwanttoinstall.run"
```
So open terminal and type "sudo sh" and then to make it easier on yourself to find the location, just drag the file into the terminal and it will insert the location of the file. Press enter, enter password if asked. Then this will start the install. You can't simply click on .run files. Hope this helps.

umm if im not mistaken that isn't how method 2 is described in that link. I don't think the method you describe works for the 4850 as mentioned on that link. Thanks for your reply though!

---

### Post by Vakman on 2009-07-11
> **fwaokda said:**
> umm if im not mistaken that isn't how method 2 is described in that link. I don't think the method you describe works for the 4850 as mentioned on that link. Thanks for your reply though!
I wouldn't worry about how it describes things for starters. Also when I navigate to that page it says "Ubuntu Hardy Installation Gui
There is currently no text in this page. You can search for this page title in other pages, search the related logs, or edit this page." Anyway, the way I said will work just fine. I have two 4850s in my machine. Just download and install :)

---

### Post by fwaokda on 2009-07-11
In that case would you mind directing me to the file you used? Also the steps you used to install? I've tried like 6 different methods and all haven't ended well... (had to reinstall) I think the method your describing was similar to one I did but I think that was the one that gave me problems with my dual monitors setup. Are you using Jaunty? Are you using 2 or more monitors? Thanks

---

### Post by Vakman on 2009-07-12
> **fwaokda said:**
> In that case would you mind directing me to the file you used? Also the steps you used to install? I've tried like 6 different methods and all haven't ended well... (had to reinstall) I think the method your describing was similar to one I did but I think that was the one that gave me problems with my dual monitors setup. Are you using Jaunty? Are you using 2 or more monitors? Thanks
Interesting. Yeah, I am using Jaunty and I think I had two monitors connected at some point but I can't be sure. The only thing I had trouble with was CrossfireX. Anyway, the file. [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) <-- Choose Linux x64 or x86, Radeon, then 4800 series. Then open up a terminal. Next type:```
sudo sh "atidriverfile"
``` I find it easier to drag the file into the terminal rather than type the location out. So "sudo sh... drag the file in" and then you just follow the installer. An alternative would be EnvyNG but we will get to that if this somehow does not work.

---

### Post by fwaokda on 2009-07-12
> **Thisislaw said:**
> Interesting. Yeah, I am using Jaunty and I think I had two monitors connected at some point but I can't be sure. The only thing I had trouble with was CrossfireX. Anyway, the file. [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) <-- Choose Linux x64 or x86, Radeon, then 4800 series. Then open up a terminal. Next type:```
sudo sh "atidriverfile"
``` I find it easier to drag the file into the terminal rather than type the location out. So "sudo sh... drag the file in" and then you just follow the installer. An alternative would be EnvyNG but we will get to that if this somehow does not work.

Alright, that's what I did last time.  I tried a different option this time and it's currently installing so I'll post back with my results.

This time I did this step instead after poking around a bit

sudo sh [atidriverfile] --buildpkg Ubuntu/jaunty

It's already started doing some extra steps with downloading more files and a couple other things...

```

Generating package: Ubuntu/jaunty
Resolving build dependencies...
Continuing package build
Package /home/usr/Desktop/xorg-driver-fglrx_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/usr/Desktop/xorg-driver-fglrx-dev_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/usr/Desktop/fglrx-kernel-source_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/usr/Desktop/fglrx-amdcccle_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/usr/Desktop/fglrx-modaliases_8.620-0ubuntu1_i386.deb has been successfully generated
Package /home/usr/Desktop/libamdxvba1_8.620-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.HBazyR

```

Now I'm not sure but I'm gonna continue installing by doing the regular command? -- oh well if not I'll come back here and redo ;)

Hope it works! ;)

---

### Post by fwaokda on 2009-07-12
So, I was able to log back in! But I think it was because nothing was installed ;(
I don't know how that happened...

Good news though! I noticed there are files on my desktop now and I've installed them. About to restart but wanted to post what they were...

fglrx-amdcccle_8.620-0ubuntu1_i386.deb  // Catalyst Control Center for the ATI graphics accelerators
fglrx-kernel-source_8.620-0ubuntu1_i386.deb // Kernel module source for the ATI graphics accelerators
fglrx-modaliases_8.620-0ubuntu1_i386.deb // Identifiers supported by the ATI graphics driver
libamdxvba1_8.620-0ubuntu1_i386.deb //AMD Unified Video Decoder library
xorg-driver-fglrx_8.620-0ubuntu1_i386.deb // Video driver for the ATI graphics accelerators
xorg-driver-fglrx-dev_8.620-0ubuntu1_i386.deb // Video driver for the ATI graphics accelerators (devel files)

I didn't know which I needed to install so I did all of them... hope that wasn't a mistake.

---

### Post by fwaokda on 2009-07-12
Complete failure... just to document after the ubuntu loading screen I get static images and it locks up.

I also tried to repair it by doing the following:
Went to recovery mode--
chose 'xfix' /* didn't help */
chose 'xfix' and 'then tried to backup with my xorg.conf.backup I made /* didn't help */

Now I'm reinstalling... then we shall try again.

---

### Post by fwaokda on 2009-07-12
Back again, This time I installed the ati driver after a clean install of jaunty and before doing any download/installs through the device manager. Then I restarted and it gave me mirrored displays BUT was at least working this time.  So I went in and set them independently of each other. Also enable the "Xinerama(?)" option to allowing dragging of windows from one desktop to the other.  Now when I start up I just have 2 black screens... anyone know how I can fix this withoutu reinstalling this time? Thanks!

UPDATE: went to recovery mode and turned of Xinerama in my xorg.conf - Now I'm able to get back in.  I went back to catalyst control panel and was able to get the proper resolution up on my main monitor. Restarted... now I have proper resolutions. I really need to get Xinerama to work though because without it ... its kinda not using dual monitors ha. Any ideas? Going to try renabling it since the resolutions are right now.

UPDATE: Xinerama still didn't load up with the desktops... just black/blank screens - although the monitors are receiving a signal I suppose because they aren't going into standby mode. Anyways I'll try and resolve this but would appreciate any advice/tips/suggestions to fixing it.  I'm going to also give it about 15mins to make sure it's not just needing some time to configure itself or something. Thanks again if you've been reading/helping!

UPDATE: 15mins later still black screen gonna go try messing with the xorg.conf now...

---

### Post by fwaokda on 2009-07-12
Alright... so here it is ladies and gentlemen the "proper" way to install ati drivers for the ati radeon 4850 hd -- so pay attention! ;)

1. Go to the Ati.com site and download the latest driver for your 4800 series card.
2. sudo sh [ati driver file name goes here without brackets] --buildandinstallpkg Ubuntu/9.04
3. sudo aticonfig --initial -f
4. Restart the system
5. Go to System>Prefs>Display and setup your monitors the way you want them.
6. Log out and back in (no need to restart again)

And you should have it working properly.  I found this solution after looking for a fix for the Xinerama problem on another post, but I forgot where the post was or who posted the solution ;(  Oh well, you know who you are and thanks!

---

### Post by Vakman on 2009-07-12
Congratulations. I guess the typical way does not work for dual monitors often.

---

### Post by morcar on 2010-02-20
> **Thisislaw said:**
> Open up a terminal. Next type:
```
sudo sh "fileyouwanttoinstall.run"
```
So open terminal and type "sudo sh" and then to make it easier on yourself to find the location, just drag the file into the terminal and it will insert the location of the file. Press enter, enter password if asked. Then this will start the install. You can't simply click on .run files. Hope this helps.

This worked for me thanks loads m8

---

### Post by Vakman on 2010-02-20
> **morcar said:**
> This worked for me thanks loads m8

Your welcome.
I was confused at when I posted this until I saw the date, since it was still in my subscribed threads.
"Whoa, this was a while ago" xD

---

### Post by Mean Mr. Mustard on 2010-03-17
This is exactly what I needed. These forums are awesome!

---

