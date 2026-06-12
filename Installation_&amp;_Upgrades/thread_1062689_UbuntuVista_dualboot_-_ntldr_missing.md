---
title: "Ubuntu/Vista dualboot - ntldr missing"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by sbruinsje on 2009-02-07
Hello,
The past 2 days i've been trying to get vista and ubuntu to dualboot. At some point it worked, but i made some changes regarding bootloaders and I messed it up. From vista I uninstalled vista bootloader (or however its named) from the MBR, as an attempt to get grub back in use. However, after this my pc wouldnt start at all and just gave me the message 'nltdr missing'. I ran ubuntu from the live cd and managed to get grub back. Now when i start I get a list with Ubuntu and vista in it. Ubuntu boots fine, but when i select Vista, it still says 'ntldr missing'.

Is there anyway I can get vista to boot again?
I have to mention that I only got a recovery disc for my laptop which will return it to the original state the laptop was in when i bought it. I don't have a regular vista installation CD.

On some other topics I saw the following info was needed to help them, so maybe you need this info about my computer too:
> 
stefan@stefan-laptop:~$ sudo fdisk -lu
[sudo] password for stefan: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0671fb49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    12992511     6495232   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    12992512   186968248    86987868+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       186973920   234435599    23730840    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       186973983   232379279    22702648+  83  Linux
/dev/sda6       232379343   234435599     1028128+  82  Linux swap / Solaris


My general setup is like this:
- One hidden service partition to restore the laptop to its original state
- One partition C:\ with vista on it.
- One partition (i believe E:\) with ubuntu on it.


Hope you can help me out.
Thanks in advance!

---

### Post by momcilosystem on 2009-02-07
The fact that you've got "ntldr is missing" is showing that grub is trying to boot from correct partition - because it has switched to windows boot.

But, since you've probably messed up vista boot, you wouldn't be able to repair it without Vista installation disk.

So, only way I can think of is to reinstall your computer using recovery disk that came with it, and then reinstall Ubuntu - because I think recovery disk erases all partitions and put them as factory intended to. 

Of course, you'll need to backup your data first

---

### Post by sbruinsje on 2009-02-07
Ah thanks for the fast reply.
Luckily I backed everything up before I started messing with the dualboot stuff.

Anyway, I could probably just download windows vista and burn it. If I have burned it on a dvd, it'll be possible to recover without formatting?

---

### Post by momcilosystem on 2009-02-07
yes it will, from vista dvd, you'll be able to recover Windows boot, then reinstall grub and you will be just fine ;)

---

### Post by 73ckn797 on 2009-02-07
Any downloaded version of Vista will probably be pirated and/or loaded with viruses, trojans and other undesirable stuff. It would also be illegal. Discussion of this nature is frowned upon in the forums and not allowed to continue. Do not be surprised to see this thread locked. You could also be banned. I am no official here but I give you fair warning.

Use the recovery already on your computer.

---

### Post by momcilosystem on 2009-02-07
Not necessarily. I managed to download genuine Vista from torrent (I use it to repair notebooks which don't have Vista installation disk with it).

You should have no problems restoring Vista boot, but in case you do, here is something to print out ;)

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)



it should be clean (if i am not allowed to post such links please edit my post)

---

### Post by 73ckn797 on 2009-02-07
You guys are on your own from here.

---

### Post by caljohnsmith on 2009-02-07
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by sbruinsje on 2009-02-08
Thanks allot for the replies guys. After the first few posts, i figured the problem would not be easy to fix, so I decided to just do a full format (sorry saw your post too late caljohnsmith, would have given it a try if I saw it in time). I got everything back in place now to the point where both Ubuntu 8.10 and Windows vista are installed on seperate partitions, and I think ubuntu is in charge of the boot list.

Currently it shows Vista and Ubuntu (+ restore stuff) and if you select nothing ubuntu wil be chosen by default. I have a few questions though:
1. Can I change it so that vista will be chosen by default, but without using vista's bootmanager?
2. If it is possible to use the ubuntu bootmanager (grub right?) to let vista be booted by default, will I have troubles with getting into vista if i uninstall ubuntu?
3. What would you suggest? use the vista boot manager or ubuntu's?

I use vista mostly, but want to have linux to learn a little about this OS. But most of the time, I probably will be using vista.

Thanks in advance!

---

### Post by dougalkerr on 2009-02-08
I dual boot with Vista and Ubuntu 8.10 and had a problem with the bootloader one day. I followed advice as below and have never looked back. It should prevent you having to reinstall anything.
Download Supergrub and burn it to a CD. A 8 cmm disc will do as it is small. Boot with Supergrub disc in drive and follow options. You will most likely get a bootloader back one way or another and hey presto!!!
Read the various help pages - it is worth it...
I used this for the first time a couple of weeks ago and now I don't leave home without it.
Good luck.

---

### Post by caljohnsmith on 2009-02-08
> **sbruinsje said:**
> 
1. Can I change it so that vista will be chosen by default, but without using vista's bootmanager?
2. If it is possible to use the ubuntu bootmanager (grub right?) to let vista be booted by default, will I have troubles with getting into vista if i uninstall ubuntu?
Sure, if you first open a terminal (Applications > Accessories > Terminal), you can open your Grub's menu.lst file with:
```
gksudo gedit /boot/grub/menu.lst
```
First I would make sure the "default X" line reads "default 0", because that means Grub will boot whichever OS is listed first in the Grub menu by default (Grub starts counting at 0, not 1). Then I would move your Vista entry at the bottom of the menu.lst just above the Debian automagic kernel lines:
```
[COLOR="Blue"]<put Vista entry here>[/COLOR]

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
Then Grub will boot Vista by default on start up.
> **sbruinsje said:**
> 
3. What would you suggest? use the vista boot manager or ubuntu's?

I would use Grub, and it's as easy as doing the above changes to make Vista the default OS to boot. Anyway, let me know how it goes or if you run into problems.

---

### Post by sbruinsje on 2009-02-08
Thanks allot, that works fine! :D

---

### Post by dougalkerr on 2009-02-08
Good to see you got yourself out o' trouble there. It might be a thought to get yourself Supergrub onto a cd all the same in case you need it for future. I always have a copy at work as well as home now.. Good luck with future OS installs...

---

### Post by caljohnsmith on 2009-02-08
> **sbruinsje said:**
> Thanks allot, that works fine! :D
Glad that worked OK; cheers and enjoy Vista and Ubuntu. :)

---

