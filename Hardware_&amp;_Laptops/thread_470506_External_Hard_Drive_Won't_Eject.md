---
title: "External Hard Drive Won't Eject"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by God_of_Belac on 2007-06-11
I'm running Ubuntu 7.04 on a Dell Inspiron 600m.  I attached via USB a Western Digital Mybook 500gb external hard drive.  Although I have not taken any action involving the drive, it will not unmount or eject.  Any attempt I make to do so, via the GUI or the terminal, produces the message "Cannot eject volume" and opens it in File Browser.

EDIT: To be clear, I unmount it in File Browser.  Its icon disappears from the desktop for a couple seconds, then the error message appears and its icon comes back.

What can I do about this?

---

### Post by nic2 on 2007-06-11
Use the following command:
```
sudo umount /media/<devicename>
```

---

### Post by vanadium on 2007-06-11
This is a bug in Ubuntu Feisty, but it should have been ironed out by now. Is your Feisty installation completely up to date? If no, update and I bet the problem will be fixed. If yes, then the issue apparently remained but you can apply a workaround that worked for me:

```

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

```

After that, the eject option for USB drives will revert to Unmount, and that is enough to be able to safely disconnect the drive physically.

---

### Post by God_of_Belac on 2007-06-11
Vanadium,
I should hope it's up to date.  I burned the live CD on Wednesday and installed the OS on Saturday.

And your workaround did not work for me.

NIC,
Your suggestion didn't quite work, but sudo umount /dev/<devicename> did.

I hope the GUI eject/unmount procedure can be ironed out.  Of all the intermittent tasks that should Just Work(tm), this is close to the front of the list.

---

### Post by floke on 2007-06-11
Agreed, but its not much of a hassle to drop to the CLI though, so it's hardly a deal breaker ;)

---

### Post by hardyn on 2007-06-15
This has been repaired though a gutsy back-ported HAL

---

### Post by uzybear on 2007-10-05
question: i hvae same problem; does it matter if i just unplug the thing?

---

### Post by newagelink on 2007-10-27
> **uzybear said:**
> question: i hvae same problem; does it matter if i just unplug the thing?I've been wondering about this as well.

I have exactly the same problem as OP -- and, as was said here, I must type "sudo umount /dev/sdb1" every time -- which gets annoying ... (But thanks so much to the cool people in the #ubuntu-offtopic IRC channel for showing me.)

Will upgrading the OS fix the issue? Why does this issue occur?

By the way, I have a Gateway laptop (Model: Gateway 6518GZ Notebook), purchased Fall 2005 (shipped July 2005, I presume from the factory). Dunno if that means anything ... Gateway Support for it appears to be centered around [http://support.gateway.com/s/Mobile/Gateway/6000Series/5051nv.shtml](http://support.gateway.com/s/Mobile/Gateway/6000Series/5051nv.shtml)

---

