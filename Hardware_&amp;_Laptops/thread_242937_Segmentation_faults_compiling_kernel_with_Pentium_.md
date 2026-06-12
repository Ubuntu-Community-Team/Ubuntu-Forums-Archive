---
title: "Segmentation faults compiling kernel with Pentium D"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by yota on 2006-08-24
I'm having an issue on my new box (a Pentium D 805 on a Asus P5ND2-SLI) running Dapper with stock kernel (2.6.15-26-686 SMP PREEMPT), if i try to compile the kernel this is what I get:
> 
yota@one:/share/tmp/linux-2.6.15.6$ make clean
yota@one:/share/tmp/linux-2.6.15.6$ make
  CHK     include/linux/version.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  SPLIT   include/linux/autoconf.h -> include/config/*
  CC      arch/i386/kernel/asm-offsets.s
  GEN     include/asm-i386/asm-offsets.h
  HOSTCC  scripts/genksyms/genksyms.o
[B]scripts/genksyms/genksyms.c: In function ‘main’:
scripts/genksyms/genksyms.c:591: internal compiler error: Segmentation fault
Please submit a full bug report,[/B]
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [scripts/genksyms/genksyms.o] Error 1
make[1]: *** [scripts/genksyms] Error 2
make: *** [scripts] Error 2
yota@one:/share/tmp/linux-2.6.15.6$

Repeated errors like this (not everytime at the same point/file) made me think that I got a broken cpu|ram|board, but I've tested (memtest, cpuburn, stressprime and many others) every single componenet in my setup and everything seems to be ok; I have no stability or other problems whatsoever.
Moreover the strange part is that if I compile with more than one job in parallel everything goes just fine!
> 
yota@one:/share/tmp/linux-2.6.15.6$ make -j8
  CHK     include/linux/version.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  SPLIT   include/linux/autoconf.h -> include/config/*
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/genksyms/genksyms.o
  HOSTCC  scripts/conmakehash
  CC      arch/i386/kernel/asm-offsets.s
  HOSTCC  scripts/bin2c
  HOSTCC  scripts/genksyms/lex.o
  HOSTCC  scripts/pnmtologo
  CC      scripts/mod/empty.o
  HOSTCC  scripts/genksyms/parse.o
  HOSTCC  scripts/mod/mk_elfconfig
  GEN     include/asm-i386/asm-offsets.h
  HOSTLD  scripts/genksyms/genksyms
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTCC  scripts/mod/modpost.o
  HOSTLD  scripts/mod/modpost
  CC      arch/i386/mm/init.o
  HOSTCC  usr/gen_init_cpio
  CC      arch/i386/kernel/process.o
  CC      arch/i386/mach-default/setup.o
  CC      init/main.o
  CHK     usr/initramfs_list
  LD      arch/i386/crypto/built-in.o
  AS [M]  arch/i386/crypto/aes-i586-asm.o
  CC      arch/i386/mm/pgtable.o
  UPD     usr/initramfs_list
  CC [M]  arch/i386/crypto/aes.o
...

Isn't this weird? How can parallel make better things?
So I bought a dual cpu but I'm forced to use every core for the same task!?! ;)

Even if this is a perfect workaround I'm still wondering what's going on, and I can't be totally confident with my setup; is someone else experiencing similar issues with a pentium d 8xx?
If I cannot spot a fault on my side I'll consider to report a bug, but first I'd like to have some other user's opinion on the matter.

UPDATE:

It seems that the problem is hardware related... I've installed the 'schedutils' package to set cpu affinity and tried to bind the compile task to one specific cpu, this are the results:
```

taskset -c 0 make --> OK

taskset -c 1 make --> KO (cpu 1 broken?)

taskset -c 1 memtest 1000m --> OK for hours (hmm... then cpu 1 not broken?)

taskset -c 0 cat /dev/urandom >> /dev/null (or anything else that puts cpu 0 at 100% usage)
and after
taskset -c 1 make --> OK (so cpu 1 is NOT broken! or it is?!?)

```
I can't understand... cpu 1 fails to compile if it's the only one working, but is able if cpu 0 is stressed too (and so 'make -j8' works just because puts also cpu0 at work).
If I do other tests on cpu 1 alone everithing is fine.

Still no guess on what does this mean... :confused: Please help!

---

### Post by yota on 2006-09-12
Bump!

Two weeks later the problem is exactly the same, I'm considering to return my cpu, but I find really strange that I've not issues in WinXP (hours of oblivion, a night with stressprime2004 and so on) or with super-pi, memtest and cpuburn under linux...

If someone out there has a Pentium D 805 can please tell me if he's able to compile the kernel using both core 0 and core 1 alone: I haven't the opportunity to test another identical cpu and such information would be really useful to me.

---

### Post by xva on 2006-09-20
I have the same cpu as you have and with ubuntu I couldn't get it recognized by the system.
then I tried the new kanotix release candidate and everything went perfectly without any configuration by me.;)

---

### Post by yota on 2006-09-22
Hi xva,

thanks for the info.
I've no problems about cpu recognition and functionalities in ubuntu: I've just installed linux-image-686 and it supports both cores and all the extensions.

Could you try to compile the kernel from source?
It would give me very valuable information, if you need any hints feel free to ask.

---

### Post by yota on 2007-02-23
Months later... just to let you know.

I've discovered it was an hardware problem of one of the cores, I've replaced the cpu and now it's all fine.

---

### Post by dannyboy79 on 2007-02-23
yota, I sent you a PM I thought but you didn't respond. I need some help because I am getting the VIA PT880 chipset with the bad AGP port. The file you mentioned to modify  prior to compiling a new kernel is pci_ids.h and it's located in 5 places:

/usr/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-27-686/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-27/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-28-686/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-28/include/linux/pci_ids.h

So I am not sure which 1 I need to modify? I have never compiled a kernel and I have no idea how to? ALso, I beleive I need to compile in SMP because I am getting the core 2 duo E4300. Can we discuss this sometime over irc chat or instant messaging? My email is [email]darfsten@wi.rr.com[/email]. please contact me I would really appreciate it.

---

### Post by pay on 2007-02-23
[Here's](http://www.howtoforge.com/kernel_compilation_ubuntu) howto compile the kernel.

---

### Post by dannyboy79 on 2007-02-23
ok but I am wondering what kernel source do I want? the guide doesn't explain how I go about chosing one. This will be for a desktop that has a XFX GeForce 6200 128mb vid card, 1.5gb of DDR ram, it's going to have a E4300 core 2 duo, it will be on the ASRock 775dual-VST motherboard which has these chipsets:
Northbridge: VIA® PT880 Pro/Ultra
Southbridge: VIA® VT8237A
(ALC888 Audio Codec)
- VIA® PHY VT6103

can't I just take the dapper ubuntu kernel source and modify that put in the support that I need for 1.5gb ram, and the core 2 duo? I also need to modify a file prior to compiling per yota to solve the agp issue due to the pt880 northbridge. the file is pci_ids.h but which 1 do I modify?

---

### Post by pay on 2007-02-23
I would say modify the one that you are using (uname -r). You can probably recompile the default Ubuntu kernel. Look in /usr/src

---

### Post by dannyboy79 on 2007-02-23
would that cause less headaches than just grabbing 2.6.20 and going from there? I don't get all the numbers. I think that this pci_id issue may be solved now in the 2.6.20 because I went thru the changelog and did a search for VIA and found this:

commit 43ed41f648554c9fecaf7597d25e05da63ec7290
Author: Dave Jones <davej@redhat.com>
Date:   Sun Jan 28 17:58:33 2007 -0500

    [AGPGART] Add new IDs to VIA AGP.
    
    Culled from the VIA codedrop.
    Also fixes up one ID used in amd64-agp to use the
    VIA part number instead of the board name in its ID.
    
    Signed-off-by: Dave Jones <davej@redhat.com>

commit 7707ea3b784195315366e6e4b5c73ca6933ff9b0
Author: Dave Jones <davej@redhat.com>
Date:   Sun Jan 28 17:50:17 2007 -0500


but I don't know if that's it or not. I can just look in the pci file after I download the source. I am only wondering why you suggest to modify the 2.6.15 kernel instead of going with the latest? If I go with latest, am I going to break stuff? iptables, samba, ssh server, and everything I have setup. See, I don't know how this kernel compiling works?? Thanks for any suggestions but if you could also provide the reasoning I would appreciate so that I can learn.

I currently have 2.6.15-28-686 as my kernel I am booting in grub.

---

### Post by pay on 2007-02-23
I mentioned recompiling the one that you already have because that is what you were asking about. If you download the latest and copy over your .config everything should be fine (actually you would be better off using a .config from feisty, I would give you mine except I have edited it.).

Another thing to remember is that Ubuntu add some binary blobs to the kernel. If you are using a wireless network then you might not want to compile your own.

If you are really worried about compiling your own kernel then I would recommend against it.

---

### Post by dannyboy79 on 2007-02-23
ok, well why would it be better to use a fiesty config. I said I have never done this and I am only trying to be informed before I do it, it's not that I am worried, like I said, I am only trying to learn before I do it. i know many people here just say, how do I do blah? then a person responds with what the code should be but never reasons why, well I am the person who wants to know why. so if you could please elaborate I would really appreciate it. thank you what are binary blobs? how would I get a .config from fiesty? again, any help would be great

---

### Post by pay on 2007-02-24
Well feisty has kernel 2.6.20 so if you used it's .config (which is a configuration file telling the kernel what it should and shouldn't compile like iptables) it would be updated for extra modules that were added since kernel 2.6.15 (kvm etc). Binary blobs are like drivers that the Ubuntu devs add. I attached a feisty kernel config for 2.6.20. Just download it to your desktop and type ```
sudo mv /home/dannyboy79/kernel_config /usr/src/linux/.config
```(assuming you extracted the kernel to /usr/src and make a linux symlink).

---

### Post by yota on 2007-02-24
Hi Dannyboy,

Good news for you: the fix has already been backported from kernel 2.6.17 to 2.6.15 (I've checked 2.6.15-27 and it's ok), so you don't need to compile your own kernel. Hopefully everything should just work.

As I can see this holds only for the 32 bits version of the kernel, while the 64 bits are still lacking support as of 16/02/2007; see [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg177919.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg177919.html) for reference. Just be sure to use a 32 bit version (686 for instance) and you're safe.

Hope this helps!

---

### Post by dannyboy79 on 2007-02-24
> **pay said:**
> Well feisty has kernel 2.6.20 so if you used it's .config (which is a configuration file telling the kernel what it should and shouldn't compile like iptables) it would be updated for extra modules that were added since kernel 2.6.15 (kvm etc). Binary blobs are like drivers that the Ubuntu devs add. I attached a feisty kernel config for 2.6.20. Just download it to your desktop and type ```
sudo mv /home/dannyboy79/kernel_config /usr/src/linux/.config
```(assuming you extracted the kernel to /usr/src and make a linux symlink).
pay, i don't see any attachment? would I just need to download fiesty and mount the iso to a folder and then look for the .config file? otherwise can you just post it again? i have broadband so it wouldn't be a big deal for me to download fiesty and I think I may try it out as a live cd on my new 775dual-VSTA motherboard by ASRock along with a E4300 Core 2 Duo. This way, if my agp 8x vid card works, than I know it's fixed in fiesty and I may chose to upgrade from dapper to fiesty. i would just hate to have to reinstall and reconfigure all that I have done. mythtv, samba, nxserver, proftpd, iptables, etc etc. Have you heard of any issues with any of these packages I have written down regarding how they work in fiesty? thanks again for any comments or help.

---

### Post by dannyboy79 on 2007-02-24
> **yota said:**
> Hi Dannyboy,

Good news for you: the fix has already been backported from kernel 2.6.17 to 2.6.15 (I've checked 2.6.15-27 and it's ok), so you don't need to compile your own kernel. Hopefully everything should just work.

As I can see this holds only for the 32 bits version of the kernel, while the 64 bits are still lacking support as of 16/02/2007; see [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg177919.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg177919.html) for reference. Just be sure to use a 32 bit version (686 for instance) and you're safe.

Hope this helps!

oh s__t man, this is awesome. I have been dreading loosing my current setup. SO I can just install the lates dapper kernel that has the 686-SMP and that will utilize both cores and allow for the 2 gigs of ram etc etc, this would be awesome then I wou;ldn't have to do waht I have bene investigating for the last week, which is compile a custom kernel. WOW, this is great if it's true.

---

### Post by pay on 2007-02-24
Opps, it said that the file was too large and I didn't notice that it didn't attach. Sorry. Here it is. It is for a generic 64bit ubuntu installation.

---

### Post by dannyboy79 on 2007-02-24
ok so that is for a 64 bit ubuntu install hey? I guess I didn't think about using the 64 bit version until you just mentioned that. I have always just used the 32 bit version since I don't have a 64 bit cpu and motherboard but now that I am getting one I guess I should consider going with the 64 bit version. Do you think it's faster? Also, what about the common issues I see in the forums about the 64 bit version? Hva eeither of you had any specific issues with the 64 bit version? I am a newbie so I wouldn't want to install it and then have issues with mythtv, samba, etc etc. Can you guys comment?

---

### Post by pay on 2007-02-25
> **dannyboy79 said:**
> ok so that is for a 64 bit ubuntu install hey? I guess I didn't think about using the 64 bit version until you just mentioned that. I have always just used the 32 bit version since I don't have a 64 bit cpu and motherboard but now that I am getting one I guess I should consider going with the 64 bit version. Do you think it's faster? Also, what about the common issues I see in the forums about the 64 bit version? Hva eeither of you had any specific issues with the 64 bit version? I am a newbie so I wouldn't want to install it and then have issues with mythtv, samba, etc etc. Can you guys comment?There have been a few threads about this already. Basically if you only use opensource software then the 64bit installation is great, but for some proprietary programs you might have some trouble but there are always workarounds.

---

### Post by dannyboy79 on 2007-02-25
well which ones off the top of your head? Is sbackup ok? nvidia video card driver 9746 for the GeForce 6200? any other's that you can think of would be great. thank you very much for all your help with this.

---

### Post by pay on 2007-02-26
The video driver should be fine. I haven't tried sbackup so I can't comment on it.
[Here's]("http://www.sabayonlinux.org/sabayon/kconfigs/SabayonLinux-x86-3.26.config") a decent x86 kernel config and [64bit]("http://www.sabayonlinux.org/sabayon/kconfigs/SabayonLinux-x86-64-3.26.config").

---

### Post by dannyboy79 on 2007-02-26
so if my agp card works with fiesty's default kernel, should I still compile my own kernal using the config you provided for 1.5 gb ram support, and the dual core, and whatever else? Also, can you comment on any programs that you specifically have ahd issues with or know of others having issues with? thanks again. Also, I noticed when I opened the x86 32 bit config, it stated this in it: 2.6.19-gentoo-r4
# Sat Dec 30 02:00:21 2006
is that what the other is 1 is for also, I didn't open it? Is this for edgy or fiesty? I guess I just thought that fiesty was the latest kernel 2.6.20? again, any more comments would be greatly appreciated. also, I would just want to put this config file within the /usr/src/ folder or is it suppose to go within a sub folder. this is what folders are within my /usr/src folder:
xxxxxxxxxx@UBUNTU:/usr/src$ ls -la
total 43636
drwxrwsr-x  7 root src      4096 2007-02-24 21:30 .
drwxr-xr-x 14 root root     4096 2006-11-27 14:16 ..
lrwxrwxrwx  1 root src        27 2007-02-23 09:54 linux -> linux-headers-2.6.15-                                                               28-686
drwxr-xr-x 19 root root     4096 2006-12-14 07:38 linux-headers-2.6.15-27
drwxr-xr-x  4 root root     4096 2006-12-14 07:38 linux-headers-2.6.15-27-686
drwxr-xr-x 19 root root     4096 2007-02-22 09:50 linux-headers-2.6.15-28
drwxr-xr-x  4 root root     4096 2007-02-22 09:50 linux-headers-2.6.15-28-686
lrwxrwxrwx  1 root src        27 2006-11-16 19:26 linux-OLDVERSION.1172246050 ->                                                                linux-headers-2.6.15-27-686
-rw-r--r--  1 root root 44605408 2007-02-01 11:43 linux-source-2.6.15.tar.bz2
drwxr-xr-x  3 root root     4096 2006-10-13 01:20 modules



thanks

---

### Post by pay on 2007-02-26
Place the config files in your linux source directory as .config. People have trouble with wine, flash and java on amd64, but you can get ALL of them to work with abit of patience. Those kernel configs were examples from sabayon Linux.> **dannyboy79 said:**
> so if my agp card works with fiesty's default kernel, should I still compile my own kernal using the config you provided for 1.5 gb ram support, and the dual core, and whatever else?If you feel brave. Don't do it if you don't know what each option is when doing make menuconfig. Good luck.

---

### Post by dannyboy79 on 2007-02-26
> **pay said:**
> Place the config files in your linux source directory as .config. People have trouble with wine, flash and java on amd64, but you can get ALL of them to work with abit of patience. Those kernel configs were examples from sabayon Linux.If you feel brave. Don't do it if you don't know what each option is when doing make menuconfig. Good luck.

well now you're confussing me even more and I know you are probably not trying to. I have explained before I have no idea how to do this so I will need to ask, why did you provide a config for sabayon Linux? when you say put it in my linux source directory, out of the ones I listed, which one is that? when I look within those folders, I noticed within each of these folders there is a file called .config:
/usr/src/linux-headers-2.6.15-27-686/.config
/usr/src/linux-headers-2.6.15-27/.config
/usr/src/linux-headers-2.6.15-28-686/.config
/usr/src/linux-headers-2.6.15-28/.config

is that what I should replace? if so, within  which subfolder or all of them? 

also, I asked this before but I don't recall it being answered, is the 64 bit version faster? for like converting avi files to dvd structure (or iso files using devede), downloading avi files, ripping my personal dvd's for backup purposes? 

Flash and java have isssues? how much work is involved in getting them working? say for a newbie, would it take an hour to fix? how would I learn what each option is when doing make menuconfig? i am brave, I came to linux to  begin with didn't I? I had a perfectly good setup with xp but I thought that I wanted to learn linux and support the open source scene so I did. Ever since March of 2006, I have been moving along at a pretty good rate I feel. I mean I have almost 1500 posts and I try to hang around the forum, I click on new posts, then anything I know I can solve I jump right in and help people out. I enjoy learning and helping.

I am sure you may be getting a little annoyed by me by now but I really appreciate your help and I hope you continue to provide me some guidance. Oh yeah, you never answered if the default kernel in edgy or fiesty provides support for my core 2 duo  as well as 1.5 gb's of ram, etc etc. thanks again.

---

### Post by pay on 2007-02-26
> **dannyboy79 said:**
> well now you're confussing me even more and I know you are probably not trying to.Sorry> **dannyboy79 said:**
> why did you provide a config for sabayon Linux?It doesn't matter what where the config file comes from. They all do the same thing.> **dannyboy79 said:**
> when you say put it in my linux source directory, out of the ones I listed, which one is that? when I look within those folders, I noticed within each of these folders there is a file called .config:
/usr/src/linux-headers-2.6.15-27-686/.config
/usr/src/linux-headers-2.6.15-27/.config
/usr/src/linux-headers-2.6.15-28-686/.config
/usr/src/linux-headers-2.6.15-28/.config

is that what I should replace? if so, within  which subfolder or all of them? When you download the source from kernel.org (which is what I was assuming you were doing) you put it in the extracted folder (probably /usr/src/linux-2.6.X)> **dannyboy79 said:**
> also, I asked this before but I don't recall it being answered, is the 64 bit version faster? for like converting avi files to dvd structure (or iso files using devede), downloading avi files, ripping my personal dvd's for backup purposes? for ripping/converting yes it should be faster for downloading movies no it won't.>  Flash and java have isssues? how much work is involved in getting them working?There are some scripts somewhere on these forums (I think aysiu made them) that take care of that.> **dannyboy79 said:**
> how would I learn what each option is when doing make menuconfig?Press the question mark (on the keyboard theres no question mark on screen) while something is highlighted.> **dannyboy79 said:**
> Oh yeah, you never answered if the default kernel in edgy or fiesty provides support for my core 2 duo as well as 1.5 gb's of ram, etc etc. thanks again.Sorry. I don't know.

---

