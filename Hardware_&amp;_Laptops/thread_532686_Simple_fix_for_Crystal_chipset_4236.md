---
title: "Simple fix for Crystal chipset 4236"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Dragonborn64 on 2007-08-23
I had problems with the crystal sound card w/chipset 4236 that was built into the motherboard in a dell optiplex gx1 computer. After looking through what seemed like thousands of pages I finally think this is what worked for me! I say think because I tried so many things and have stayed up most of the night trying to fix this computer that it gets a little fuzy! But I am reasonably sure that this is the last thing I tried before I got my sound card to work!

I opened a terminal and typed  sudo modprobe snd-cs4236 after which I got the following printout in the terminal ....................

jack@jack-desktop:~$ sudo modprobe snd-cs4236 
Segmentation fault 
jack@jack-desktop:~$ 
Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733448] Oops: 0002 [#1] 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733455] SMP 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733671] CPU:    0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733676] EIP:    0060:[kobject_add+102/416]    Not tainted VLI 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733682] EFLAGS: 00210292   (2.6.20-16-generic #2) 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733704] EIP is at kobject_add+0x66/0x1a0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733716] eax: 00000001   ebx: e0bd45f8   ecx: e0b797b0   edx: e0bd4614 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733731] esi: e0bd45fc   edi: e0bd45f8   ebp: fffffffe   esp: d4d19e68 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733743] ds: 007b   es: 007b   ss: 0068 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733756] Process modprobe (pid: 24070, ti=d4d18000 task=cf5d7030 task.ti=d4d18000) 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733766] Stack: e0bd45fc e0bd45fc d4d19ea4 e0bd45f8 c03b3260 e0bd45f8 ffffffea e0bd45f8 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733795]        c03b31e0 c01edb51 00000000 e0bd45e0 c02572fe e0bd45f8 c036522a e0bd18ce 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733823]        e0bd45e0 00000020 e0bd45a0 cad2921c 00000017 c022a6bd 00000020 e0bd5500 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733850] Call Trace: 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733902]  [kobject_register+33/80] kobject_register+0x21/0x50 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733929]  [bus_add_driver+110/416] bus_add_driver+0x6e/0x1a0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.733993]  [pnp_register_card_driver+77/176] pnp_register_card_driver+0x4d/0xb0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734029]  [<e084607a>] alsa_card_cs423x_init+0x7a/0xd0 [snd_cs4236] 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734076]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734277]  [sys_mmap2+205/208] sys_mmap2+0xcd/0xd0 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734336]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734422]  ======================= 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734429] Code: e8 00 0f 10 00 8b 4c 24 10 85 c9 0f 84 3b 01 00 00 8b 43 28 8d 53 1c 83 c0 08 8b 48 04 89 43 1c 89 50 04 b8 01 00 00 00 89 4a 04 <89> 11 8b 53 28 83 c2 10 86 02 8b 13 31 ed 8b 44 24 10 85 d2 89 

Message from syslogd@jack-desktop at Thu Aug 23 00:50:31 2007 ... 
jack-desktop kernel: [462855.734547] EIP: [kobject_add+102/416] kobject_add+0x66/0x1a0 SS:ESP 0068:d4d19e68 
jack@jack-desktop:~$ 

after all this I rebooted my system and I typed  sudo modprobe snd-cs4236  into the terminal again and I could finally open the volume controls and preferences and when I tested sound playback I heard a beautiful loud shrill coming from my speakers.
I did not have to change any files manually, it all happened when I rebooted my computer!

Hope this helps, but if not send me a message and I will investigate farther to find out what else I did to get it to work! But I am pretty sure that this is all it took!

~Dragon~

---

### Post by Dragonborn64 on 2007-09-03
I  have come to the realization that I must have made a terrible mistake in my first post to this Forum! After having the same problem with my Dell Optiplex GX! computer, I began the process of repairing my computer using the material I 


I had to reformat my computer again and had the same sound problem I had the first time I installed Ubuntu! This time I realized that my first post was in error, since I have learned more since my first post!

I was playing with the terminal, and typed

"snd" (Enter) 

into the terminal and received this message ...... 

program 'snd' is currently not installed.  You can install it by typing: 
sudo apt-get install snd-gtk. Make sure you have the 'universe' component enabled

So I typed ....

desktop:/$ "sudo apt-get install snd-gtk" (Enter)
Password: "password" (Enter)

and received the following text ,,,,,,,,,,,,,

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  fftw3 libfreebob0 libgsl0 libgtkglext1 libjack0.100.0-0 libsamplerate0 snd 
Suggested packages: 
  fftw3-dev gsl-ref-psdoc gsl-doc-pdf gsl-ref-html snd-doc 
Recommended packages: 
  jackd guile ladspa-plugin 
The following NEW packages will be installed: 
  fftw3 libfreebob0 libgsl0 libgtkglext1 libjack0.100.0-0 libsamplerate0 snd 
  snd-gtk 
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded. 
Need to get 4407kB of archives. 
After unpacking 14.6MB of additional disk space will be used. 
Do you want to continue [Y/n]? 


desktop:/$"y" (Enter) and then received ...............

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main fftw3 3.1.2-1build1 [1043kB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libfreebob0 1.0.0-3 [147kB] 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgsl0 1.8-3build1 [776kB] 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgtkglext1 1.0.6-2.1ubuntu1 [110kB] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libjack0.100.0-0 0.102.20-1 [88.4kB] 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libsamplerate0 0.1.2-2 [108kB] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe snd-gtk 7.18-2 [985kB] 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe snd 7.18-2 [1150kB]         
Fetched 4407kB in 10s (408kB/s)                                                
Selecting previously deselected package fftw3. 
(Reading database ... 121768 files and directories currently installed.) 

just for shucks and giggles I typed 

I went ahead and typed

desktop:/$sudo modprobe snd-cs4236
Password:"password"

since I received no error messages, just for shucks and giggles I went ahead and took a leap of faith and entered the following into the terminal ......

desktop:/$ "ALSAMIXER"

and guess what? ............................. ALSA's mixer popped up on my screen and my computer finally had sound coming out of the speakers! 

So my previous post had to be wrong, and it seems that this post shows the best way to fix the sound problem I was having with the old Dell Optiplex GX1 dinosaur, which I and at least a few others in this forum are using! 

Now not only do I freely admit to being a complete noob with Ubuntu, but also with the whole Unix/Linux experience and community on the whole!  A month from now after I learn more about Ubuntu/Linux, I may realize that I was totally wrong with my assumptions once again, but I feel more confident this time than I did on my last post!!

 When I posted the first message unlike this time, I had no idea that the Ubuntu/Linux modules were virtually the same as the drivers and DLL's I was so comfortable working with in Windows! So I guess that I am learning quite a bit about Ubuntu and Linux after all! And no matter how lost I may feel at times, stumbling through the twilit of this “strange” new world I find myself in! I am actually learning about the Unix/Linux operating system at a much greater rate than I ever did while trying to learn about Microsoft's Windows O.S!

And the reason is because of the Ubuntu Community, and the fact that I am not just sitting here alone trying to learn, but I have the help and knowledge of all those that came before me! That is why I am trying so hard to learn and hopefully be of some help to those who come after me, because of the loyalty and respect I feel towards this place I now call home!

Dragon64   :P

---

