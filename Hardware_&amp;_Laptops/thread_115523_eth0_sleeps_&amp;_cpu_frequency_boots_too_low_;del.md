---
title: "eth0 sleeps &amp; cpu frequency boots too low ;dell insp 8200"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by disciple on 2006-01-10
hi,
i've got an Inspiron 8200 1.7Ghz P4m, with a 3com  3c905 TX  at eth0 ( used to connect to a Speedstream 5200 dsl modem, which assigns a dhcp address) and an intel 2200BG mini pci wifi at eth1 ( which i have not tested yet)

upon my intial install of kubuntu two weeks ago ( after years of fence sitting on the linux question)  eth0 worked well.. but eventually the connection began to drop.. seemed as if it ( eth0)  was hibernating..  took off ACPI via 'acpi = off' in  grub and in the bios, yet it still does this..also, after acpi was removed, the internet connection at eth0 is always inactive after KDE boots, ( though it resolves the time with the ntp server during the  initial boot)

to get eth0 back up, i use   
sudo ifup eth0 ;sudo ifconfig eth0; dhclient eth0;   

these are the steps i saw in the forum to resolve other connectivity problems, but it does not resolve it permanantly..

after some time this will work.. but is sort of frustrating repeating it for up to  15 minutes at times..  and then it still drops during regular use


also, the cpu booted up ~ 1100 mhz, and i had to manually step it up to ~1700 mhz with powernowd

tried cpufred, and it's the same thing..

so, my main problems are 
1) eth0 behaving a bit erratically  (coming to think of it.. this happened after i updated to kde 3.5.. the first time i noticed it happened, i immediately reinstalled, thinkin that i had messed something up big time..lol. that's years of windows training, right there..)

2) need to step my cpu up to its maximum permanently

thanks, everyone, in advance for your time

---

### Post by kcr on 2006-02-01
[QUOTE=disciple]hi,

so, my main problems are 
1) eth0 behaving a bit erratically  (coming to think of it.. this happened after i updated to kde 3.5.. the first time i noticed it happened, i immediately reinstalled, thinkin that i had messed something up big time..lol. that's years of windows training, right there..)

[/QUOTE]

I have the same problem on my 8200 - I ended up disabling the inbuilt ethernet and getting a PCMCIA Card. The internal port had worked fine under 5.04 then it all went bad after a kernel update. 

It had also worked fine under previous versions mandrake and redhat - 

I'd get the PCMCIA Card - for the quick fix. 

Does it work under knoppix?

---

### Post by disciple on 2006-02-01
hmm..well it didn't have to come to purchasing another card, thankfully. :-) 

I upgraded to kde 3.5.1 last night, and the problem disappeared.. 

(i re-enabled ACPI, as well, and eth0 still not givin trouble)

don't know it this alone solved the problem, i also upgraded the kernel a couple days before to 2.6.12-10-686 .. but i really think it was KDE alone , since it was working fine before 3.5.0, and is working now with 3.5.1 


with regards to knoppix, i'm not too sure..

i tried damn small linux and various ubuntu live cds in the recent past, and they didn't want to bring up eth0. 

i don't know if this is by design ?

still no luck with setting the frequency permanently yet..
by chance do you use i8kutils?  

each time i restart, i need to use modprobe to load it...

i'm guessing i'd have to recompile the kernel with i8k included, if i want to load it automatically, but is there another way?

---

### Post by kcr on 2006-02-02
[QUOTE=disciple]
still no luck with setting the frequency permanently yet..
by chance do you use i8kutils?  

each time i restart, i need to use modprobe to load it...

i'm guessing i'd have to recompile the kernel with i8k included, if i want to load it automatically, but is there another way?[/QUOTE]

I don't use i8k - I did a year or so ago so that I could get at the Multimedia keys going - but ubuntu has hotkey now so the multimedia keys work out of the box. And when I did use it I didn't like the way you could switch the fans off - noisy as they are on the 8200 they are reassuring.

If you want to get it the module to load automatically you just add 'i8k' to the end of /etc/modules - I think I haven't tried it. 

This again doesn't answer your question but have you played with the gnome CPU Frequency applet - I was worried about the speed step thing but when you have the applet running you can see the CPU pick up speed when things get busy and drop off when you are not doing much. Reassuring if you don't think you are getting enough performance.

I'll play with knoppix when I get some time and report back.

---

### Post by disciple on 2006-02-05
[QUOTE=kcr]
If you want to get it the module to load automatically you just add 'i8k' to the end of /etc/modules - I think I haven't tried it. 

[/QUOTE]


thanks!!! it worked :mrgreen: 


oddly enough, i tried the 'damn small'  live disk again, ( i fudged up my install the day before, and had to reinstall kubuntu

and eth0 was working

weird..lol

---

