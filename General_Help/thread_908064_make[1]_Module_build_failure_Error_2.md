---
title: "make[1] Module build failure Error 2"
date: 2008-09-02
forum: General Help
---

### Post by amoun on 2008-09-02
Hi I'm having a problem installing a dial-up modem (Zoom 3095). I have posted the details on an 'old' post about the Zoom modem, but have had no reply.

I thought rather than address the modem problem I may be able to fix if if I understood what the problem is in terms of understanding the language.

I have searched for info on the issues ( make etc) but have drawn a blank.

So is there anyone that can talk me through  modem-buildlog.txt
```
(cd /lib/modules/2.6.24-20-eeepc/build &&
 make "CNXT_KERNELSRC=/lib/modules/2.6.24-20-eeepc/build" 
"M=/usr/lib/dgcmodem/modules" "CC=gcc" clean)

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-eeepc'

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-eeepc'

rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd 
GPL/.*.cmd .tmp_versions .tmp_versions  
/lib/modules/2.6.24-20-eeepc/build/.tmp_versions/dgcusbdcp.mod Modules.symvers 
GPL/hda/Modules.symvers

(cd /lib/modules/2.6.24-20-eeepc/build && 
make "CNXT_KERNELSRC=/lib/modules/2.6.24-20-eeepc/build" 
"M=/usr/lib/dgcmodem/modules" "CC=gcc" modules)

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-eeepc'
scripts/Makefile.build:46: *** 
CFLAGS was changed in "/usr/lib/dgcmodem/modules/Makefile". 
Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-eeepc'
make: *** [all] Error 2
```
[LIST=1]
[*]Why does make have a [1] suffix
[*]Why does it enter and leave and yet appear to do nothing in bewtween
[*]What are the three * '***'?
[*]Fix it to use EXTRA_CFLAGS.
[*]make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2
[*]make: *** [all] Error 2
[/LIST]

Thanks

---

### Post by robertsdf on 2009-06-17
hi amoun - any information on the module build failure error 2? I just upgraded one of my computers to U 9.04 and I can not get the dgcmodem to run for the Zoom 3095

---

### Post by amoun on 2009-06-17
> **robertsdf said:**
> hi amoun - any information on the module build failure error 2? I just upgraded one of my computers to U 9.04 and I can not get the dgcmodem to run for the Zoom 3095

Hi Robert. Was it ok on an earlier version. I'm still using Hardy.

The problem was resolved by asking a friend who is more LINUX savvy than me. I know very little.

If I remember correctly, the problem was that one of the paths was incorrect and had to be altered.

When I see my friend I'll see what he can remember. He did it so quickly I couldn't remember.

Its one reason I don't want to upgrade from Hardy. 

If I don't update within a few weeks and you've not sorted it, remind me.

---

### Post by alpage2 on 2009-07-02
Hi Amoun

I have exactly the same problem. It would be a big help if your friend could identify exactly what he changed, and you could post it here to this thread.

Thanks in anticipation
Alan

---

### Post by amoun on 2009-07-03
Hi. Thanks for the reminder. I haven't seen my friend yet but by going over the above it has initiated some memory. I will try and confirm the following so try this with a backup copy. I will also try and find the amended files on my ASUS EEEPC.

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-eeepc'
scripts/Makefile.build:46: *** 
CFLAGS was changed in "/usr/lib/dgcmodem/modules/Makefile". 
Fix it to use EXTRA_CFLAGS.
```

If I remember correctly the Makefile file had to be opened and the cases of CFLAGS were changed to EXTRA_CFLAGS.

I also had to find the name of the modem and select it before my ppp would use it.

I'm not on this forum much as I'm busy out in the fields. Veganic agriculture is my occupation, and I have only a couple of 25 year old solar panels and batteries to keep this alive, but I will get back to you. :)

---

### Post by amoun on 2009-07-03
Ok I have found the file, it was as I had remembered. I've ftp'd it to 
[http://rogerlovejoy.info/opensource/zoom3095/](http://rogerlovejoy.info/opensource/zoom3095/)

I'm not that savvy with the deb methodology but I think after a failed install I have a /[urs/lib/dgcmodem/modules] folder. 

Copy the Makefile to backup and replace with the one from my site above.
Then rerun the install in the setup from a command terminal rather than the original.

I'm not sure about the above method but hopefully you know more about that than I do, or someone else will, and I will still contact my friend to walk me through the method.

All the best

Amoun

---

### Post by alpage2 on 2009-07-03
Thanks for that, Amoun.

I tried your makefile, but it threw errors.

I tried converting all instances of CFLAGS to EXTRA_CFLAGS in the original make file, but it still ends with the same error messages.

I am still open to ideas from anyone who knows the solution....

Alan

---

### Post by amoun on 2009-07-03
Hi Alan
What pc and os are you using (mine is asus eeepc 900 and hardy)
I am thinking of trying 9.04 on my old Dell Inspiron 4150.
Will post the effort etc.

Amoun

---

### Post by alpage2 on 2009-07-03
I am running the ubuntu netbook remix (9.04) on an acer aspire one: 1GB RAM and 16GB solid state drive.

Alan

---

### Post by khajavi on 2009-11-16
> **alpage2 said:**
> I am running the ubuntu netbook remix (9.04) on an acer aspire one: 1GB RAM and 16GB solid state drive.

Alan

me too, I have ubuntu 9.04 with eeepc 1000he
and I have this compile time error

---

