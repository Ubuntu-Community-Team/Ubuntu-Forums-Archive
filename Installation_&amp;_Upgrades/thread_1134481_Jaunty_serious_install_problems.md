---
title: "Jaunty serious install problem/s"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-04-23
I am still new to Linux but, after buying a new laptop and installing Ubuntu 8.10 64 bit and upgrading as and when available I had a lovely almost fully functional system with Cyberlink PowerDVD not running through Wine properly being the only thing that was letting my experience down as I can't watch any commercial DVDs. Small price to pay for something that is otherwise very nice to look at and use, with Compiz fully operational adding to the good experience.
So, now for the down side. Updates were available tonight with the offer of upgrading to Jaunty. I proceeded (no fear) and the files were downloaded. The system just seemed to sit there after the files were downloaded with no signs of installs taking place after half an hour. So I rebooted. The updates notification icon was showing and I proceeded with a warning that a partial upgrade was a choice. I continued and the system finished downloading one further file out of the 782 files if I remember correctly. So there was a message displayed before I could conti nue saying it was "imperative to run liloconfig and execute cd /sbin/lilo after liliconfig" or lilo wouldn't work.
If memory serves me well Lilo is a boot menu similar to Grub - yes?
So, I click the forward button (only other option is to cancel).
The upgrade to Jaunty continues and the system reboot is required.
Well Grub shows the boot list as before - I choose my last Ubuntu configuration and the Ubuntu splash screen shows with the animated bar and after about 20 seconds or so I get the following displayed;

Boot from (hd0,5) ext3 4c3133d3-2953-47fb-b4b8-4076a6bf3f07
Starting up ...
Loading please wait ...
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the root device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4c3133d3-2953-47fb-b4b8-4076a6bf3f07 does not exist. Dropping to a shell!

BustBox v1.10.2 (Ubuntu 1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

So, I type in liloconfig as I believe this may be wanted as described when Jaunty was to be installed but all the time in the back of my mind I am thinking that there is something wrong with the file system missing root. Anyways, system returned;

/bin/sh: liloconfig: not found.
(initramfs)

I type cd sbin/lilo "again not expecting much and I was right. System returned:)

Couldn't cd to sbin/lilo.

I typed ls and sure enough the folders are not there and neither is liloconfig (not even a lilo folder). Result of ls is;

dev var scripts lib64 lib etc sys tmp root init usr bin conf sbin proc

Looks like I will have to download and burn an install cd using 'Windows'!!!!!!!! - yuck. Doesn't matter how much I dislike Windows I seem to keep coming back to it as always being there for occasions like this. Boy am I glad I kept it as a dual boot option. I am sincerely wanting a purely Linux experience but, my faith is being stretched. The recovery options available on Grub will do nothing either so for me it seems I have lost my Ubuntu install.
How can I prevent such a catastrophic failure of an Operating System install losing my present system. It I did not have Windows on here just now I would have to reinstall Ubuntu to be able to get onto the Internet again and type out my experience to you guys and look for help and advice.
So, bottom line? Is Jaunty safe to use or not. Do I bother with trying to burn a cd and try again. I can imagine like a lot of people I always want the most up-to-date system running. How do I prevent having to reinstall the whole system again if problems like this occur. I am willing to listen and learn...

---

### Post by riza hylviu on 2009-04-23
hi
upgrading the os to another version sometimes has some issues, a clean install is best choice. Now you cannot turn back so i think it is better to go ahead and reinstall jaunty. I don't think you will have problems with the clean install, but there may still be some bugs that will be fixed in this month. 
Why you couldn't watch dvds in intrepid? You don't need powerdvd for watching them, mplayer with the libdvdcss2 codec would be enough.

---

### Post by JK3mp on 2009-04-23
Yeah you should've been able to watch dvds in any player if you had the proper codec's installed. Also above post is very correct. Clean install always seems the best way to go. If you can get to anyshell and recover anything do so then just fresh install. Sorry you had issue's. Hopefully i won't with my install of what sounds like a great up for ubuntu.

---

### Post by dougalkerr on 2009-04-24
Thanks for the encouragement guys. Have been sent the command for getting the codecs for vlc so, much fun a comin' soon I hope...

---

