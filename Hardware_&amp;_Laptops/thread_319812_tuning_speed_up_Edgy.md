---
title: "tuning: speed up Edgy"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by deadlinx on 2006-12-16
Hi, 

I'd like to speed up my brand new Edgy installed on my laptop.

I'm used to start, at boot time, only necessary scripts (such as acpi, frequency scaling..) so I kill scripts I think are unuseful or not necessary at boot time.

I'm not a seasoned Ubuntu geek so I'd like to kill some scripts in /etc/rc2.d and /etc/rcS.d but I'd like to "hear" your opinions 'cause I don't know the new Ubuntu boot style very well.

I think I can also kill, without problems, these scripts in /etc/rcS.d:

cupsys --> printer
hplip    --> hp printer
rsync --> rsync daemon
bluetooth --> bluetooth daemon
usplash  --> splash image @ boot
rc.local  --> personal boot script
anacron --> similar to cron
festival --> voice server
hotkey-setup --> special keys for laptops, I never used special            
                                                                              keys

I renamed with K all these scripts in /etc/rc2.d, thay are not so useful at boot time for my laptop.

I think I can also kill, without problems, these scripts in /etc/rcS.d:

pcimciautils  -> 'cause I don't use pcimcia port
brltty  --> 'cause I don't need to use Braille ;-)
dns-clean --> 'cause I don't use a dial-up connection
ppp-dns --> 'cause I think it's obsolete
mountnfs-bootclean --> 'cause I've not NFS file systems
waitnfs --> same reason
checkfs --> 'cause it takes time and I think it's not necessary at  
                                                                         every boot
checkroot --> same reason, it could be useful every 30 boots or 
                                                               something like this.


Please, give me a feedback, what you think about killing these processes? I think it's secure, no possible problems, and the boot time should be something like 12 secs faster!

Thank you in advance,

deadlinx

---

### Post by zgornel on 2006-12-16
Yeah, you can pretty much kill'em. Check also rc5.d, for the 5 (X) runlevel.

---

### Post by deadlinx on 2006-12-16
Hi,

I'm using the default Ubuntu runlevel that is the second so I think it's sufficient to modify rcS.d and rc2.d, why you wrote about rc5.d?

Thank you,

deadlinx

---

### Post by zgornel on 2006-12-16
The default runlevel is 5 (X session).

---

### Post by speedman on 2006-12-16
> **zgornel said:**
> The default runlevel is 5 (X session).

No it isn't.  Debian based distros (like Ubuntu) default to run level 2 and either start a display manager, such as gdm, or not.  Only Red Hat (and it's derivatives) use run level 5 for X.

Check the output of:

who -r


SM

---

### Post by zgornel on 2006-12-16
You're right. :D .

---

### Post by deadlinx on 2006-12-22
> **zgornel said:**
> Yeah, you can pretty much kill'em. Check also rc5.d, for the 5 (X) runlevel.

Hi,

I think there's something wrong in this reply:

1- Ubuntu starts with runlevel 2 by default, as I've just written.

2- With Edgy some boot scripts moved from /etc/rc2.d to /etc/rcS.d such as brltty.
    
    Apart scripts originally lying in /etc/rc2.d it's not sufficient to rename the script, in /etc/
    rcS.d, if we don't like it to start at boot time.

    The reason is lots of scripts in /etc/rcS. have dependencies, it means if you don't want  
    this process at boot time you have to rewrite scripts not just rename them.


For instance it's not necessary to check filesystems everytime at boot so we could desire to disable the script checkfs.sh 'cause we are not interested in controlling other filesystem, apart root one, unfortunately this script has dependencies so the only way to disable it is to redesign and rewrite scripts depending on it.

I consider this procedure of rewriting but it takes a lot of time, so nevermind I'll use more often hibernation.

I can gain time with a little "trick": I remove all partions in /etc/fstab, except root and swap, so the script still remain at boot time, but it doesn't have partion to check!

I hope this could be useful,


deadlinx

---

