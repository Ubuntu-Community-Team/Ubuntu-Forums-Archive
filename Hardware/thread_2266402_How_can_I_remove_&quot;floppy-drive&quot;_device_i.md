---
title: "How can I remove &quot;floppy-drive&quot; device in 14.10?"
date: 2015-02-22
forum: Hardware
---

### Post by aqk on 2015-02-22
Hi -   
Just a minor annoyance- 
 
I just upgraded an old Ubuntu 13.04 to the latest 14.10
I notice a device-  "Floppy disk" on the side when I display my files with the FILES icon.
How do I remove this non-existent device from the system?
 (I haven't had a floppy drive on a system in 10 years!)

I already commented out the following line in  my  [B]/etc/fstab  - 
    #  WTF....? /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0  [/B]

and then rebooted- but this annoying "floppy drive" line is still there.

---

### Post by Bashing-om on 2015-02-22
aqk; Hello;

Disable "floppy seek" in your bios.
Bios hands that parameter off to the kernel. ( and as well leave the 'mount' disabled in the fstab file)

[INDENT][INDENT]been there
[INDENT][INDENT][INDENT]done that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aqk on 2015-02-22
Of course!  (hand slapping my forehead)
I haven't lookat the BIOS since way back when... 

Thanx!

---

### Post by Bashing-om on 2015-02-22
aqk; Hey hey ...

It all begins in bios .

If that resolves this little situation;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we see what 
[INDENT][INDENT][INDENT]the next time ( see ya here !)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aqk on 2015-02-22
**[SIZE=4]I spoke too soon![/SIZE]**
There IS NO "floppy" or diskette device in my BIOS, as far as I can see...   :mad:

---

### Post by Bashing-om on 2015-02-22
aqk; Now that just is not right .

I run Phoenix as my bios .. and I assure you that the setting is there . Maybe take a look on-line and see if you can find 'your' bios manual ?

It does, it does
[INDENT][INDENT]all start in bios
[/INDENT][/INDENT]

---

### Post by aqk on 2015-02-22
Well,    
  **[SIZE=3]sudo modprobe -r floppy[/SIZE]**
 seems to work.. until the next reboot. 
Now- how do I make this permanent? Well...

I added  **[COLOR="#FF0000"]modprobe -r floppy[/COLOR]**  to the  /etc/rc.local  file. This seemed to do the trick!
E.G.  **[COLOR="#FF0000"]sudo gedit /etc/rc.local[/COLOR]**

---

### Post by aqk on 2015-02-22
Sorry, but lots of "newer" BIOSes no longer incude a floppy drive. 

In my case it's an AWARD BIOS from 2011...

Anyhow I solved my problem - see below

---

