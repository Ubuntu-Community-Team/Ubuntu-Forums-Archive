---
title: "[SOLVED] NVIDIA driver can't find the installed linux-libc-dev"
date: 2008-11-29
forum: General Help
---

### Post by HousieMousie2 on 2008-11-29
With the new linux-image update comes the reinstalling of the special NVIDIA driver I need, since my card will not work with the restricted drivers, and vesa is not a compromise I am willing to endure...

Unlike other kernel updates, this time my NVIDIA driver is giving me fits.

This time it keeps asking for the libc-dev headers... which I installed.  I have rebooted several times, including a cold start... but no change.

Tried using the previously working driver as well as the newest one for my card, NVIDIA-Linux-x86-177.80-pkg1.run and NVIDIA-Linux-x86-177.82-pkg1.run, respectively... no change.

Not crazy about having to use the older kernel, but if no other option comes to light, I will.

Anyone running into this also?  Any cures?

Thanks.

---

### Post by PmDematagoda on 2008-11-29
Did you install the build-essential package with:-
```
sudo apt-get install build-essential
```
and then try running the driver setup?

But before all that, did you try installing the Nvidia driver through the repositories?

---

### Post by HousieMousie2 on 2008-11-29
None of the drivers I have tried have worked, envy, envyng, glx-new, glx-legacy and so on... nor has swapping "nv" for "nvidia" in the config.

I have an nVidia GeForce 9600 GT xfx Alpha Dog edition video card.  lol  We could both go blind reading all of the posts from people having trouble with this series of nVidia cards.

I have not tried: sudo apt-get install build-essential

Sounds promising.

What will it do... and hopefully not undo? lol

((EDITED: Sorry, if I seem 'gun shy'... I am, but I would also like to learn from this, not just a blindly follow commands, but to understand them as well.))

((Second Edit:  Did some poking around about build-essential... then did it.  Here are the results

```
:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 8008kB of archives.
After this operation, 30.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

Should I also install the 'suggested packages'?

---

### Post by HousieMousie2 on 2008-11-29
Back to the drawing board...

It 'seemed' like it went well, it didn't complain about libc, but it wouldn't boot into a graphical mode... and the text mode kept blacking/blanking out while I was trying to log in/password and try to use the command line.

Neither the new kernel, nor the old one work now unless I add 'xforcevesa' to the boot line.

I wasn't seeing any red text during the boot... but since Upstart doesn't log the actual boot messages, who knows.

---

### Post by PmDematagoda on 2008-11-29
Did you install the nvidia-glx packages by any chance?

---

### Post by HousieMousie2 on 2008-11-29
Not any time recently... I am working with a fresh install... except for my /home partition.

The only thing Adept reports as being installed is the nvidia-kernel-common.

---

### Post by PmDematagoda on 2008-11-29
Remove all nvidia* packages and then try installing the Nvidia driver.

---

### Post by HousieMousie2 on 2008-11-29
Well, after removing nvidia-kernel-common, the install of the driver looked as if it failed... but it restarted fine and seems to be working correctly.

Strange, but fine with me, so long as it works.

Thank you, PmDematagoda

---

### Post by ubu84 on 2008-12-02
What driver are you using HosieMousie2?  I'm about to write ubuntu to a cd just so i can piss on it for all the trouble with trying to get my 9600GT working.  Everytime I try and install or uninstall a driver it tells me nvidia-glx-new can't be found.  I saw the question above about installing the glx drivers, so I did this:

apt-get remove nvidia-kernel-common

Even this complained about not being able to remove nvidia-glx-new.  

Did you get the driver from the nvidia website?

---

### Post by HousieMousie2 on 2008-12-02
ubu84,

lol @ CD

Yes, I got the driver from the nvidia web site.

I am using:

NVIDIA-Linux-x86-177.82-pkg1.run

I have never run into the problem of an nvidia driver complaining about not being able to find something until this last time... well, except for a kernel module, but that happens every time.

Let me know if there is any information I might be able to provide you.

---

### Post by ubu84 on 2008-12-07
HousieMousie2,

I feel a bit dumb for not noticing this before, but I think my problem with my geforce 9600GT was that I was using vmware on a windows machine.  I think vmware was not allowing the nvidia-installer to access one or more files, which prevented the installer from detecting my card.

I gave in though and pulled out my old box that has a geforce 8800GS.  Did a clean install (not using vmware or any of that jazz) and everything is working fine now.

Thanks for your help man.

---

### Post by HousieMousie2 on 2008-12-07
Sorry to hear you didn't/couldn't get your 9600GT running.

Aside from the habitual reinstalling of the driver with every new kernel image, (which, barring weirdness, I can almost do with my eyes closed now) I am very happy with mine... now if I could just get a good driver for my sound card. **deep sigh** lol Oh well.

I haven't used vmware, no clue what it is or does, but it sounds like you are happy now and that's great!

Cheers and may the Schwartz be with you!

And thanks for giving me something else to look up... hmmm... vmware... **pokes it with a stick**

---

