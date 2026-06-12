---
title: "orinoco monitor mode problem"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by tobsen on 2005-10-27
first of all I like to say HELLO to the community :-) !
I am new in this forum and I am new to ubuntu. before ubuntu I used freebsd on my notebook but it was not that "easy going style" that I expect to get for my workstation. so I tested ubuntu as a friend told me that it is working very well and it is nicely to configure. so I installed it, rebooted und then WHAM  ! Gnome was running out of the box, sound, cpu freq changing, network, modem... everything went well DIRECTLY ! ubuntu ROCKS :-) !!! and I look forward to use it [ but my server runs freeBSD and nothing in the world can make me change that :-) ]

and now i come up with my first, serious problem.
I can not get the monitor mode on my orinoco gold card working. i dont know why and I read a lot in this and in other forums.
I tried it as described in here [http://ubuntuforums.org/showthread.php?p=427388#post427388]("http://ubuntuforums.org/showthread.php?p=427388#post427388")  
It seemed to work well cause no error came up, but the monitor mode was not working. I tried then different drivers and patches, nothing helped.

may be I do not get the compiled driver to the right location ? hmm
may be it is the firmware ( well I think it is the firmware, but what can I do ?)
I tried the newest driver [http://airsnort.shmoo.com/orinocoinfo.html]("http://airsnort.shmoo.com/orinocoinfo.html")
cause they write that no patch is needed, but when I compile and use it the system comes up with the error --> dmesg | grep orinoco 
> [4294730.589000] orinoco: disagrees about version of symbol struct_module
[4294730.602000] orinoco: disagrees about version of symbol struct_module
[4294730.602000] orinoco_cs: disagrees about version of symbol struct_module 


any suggestions ?

please somebody may help me :-)

[ SYSTEM I AM RUNNING: Toshiba Notebook, Ubuntu 5.10 , Orinoco GoldCard ]

---

### Post by az on 2005-10-27
What about the hostap driver?  I think it is really stable and has been around for a very long time.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hostap&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hostap&searchon=names&subword=1&version=breezy&release=all)

---

### Post by tobsen on 2005-10-27
Hey ho I got it working ! 

well I did not try the hostap driver, cause I do not have a Prism2 or something like that chipset, it is a Hermes I.

but then I found this [http://forums.gentoo.org/viewtopic.php?t=264219]("http://forums.gentoo.org/viewtopic.php?t=264219")
and it worked very well for me :-) YESS !!! I love mr . hashier !

greets and thx 
bye

---

