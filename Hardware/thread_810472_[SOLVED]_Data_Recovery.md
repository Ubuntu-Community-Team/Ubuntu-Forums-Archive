---
title: "[SOLVED] Data Recovery"
date: 2008-05-28
forum: Hardware
---

### Post by devinWhalen on 2008-05-28
Hello,


I had a harddrive fail the other day that had Ubuntu installed on it.  I bought a new harddrive and installed the latest version of Ubuntu on it and now I am wondering about data recovery.

I am going to try to set the old failed drive as a slave and then see if Ubuntu will recognize it when it boots up.  Is there any risk to doing this?    What about any special software to try to get the data off?

Thanks for any help

---

### Post by Mark_in_Hollywood on 2008-05-28
I have had to do this several times. 

MAKE CERTAIN THAT THE TWO DRIVES ARE BOTH JUMPERED AS 

CABLE SELECT

If you cannot boot from your known working drive after installing the 2nd drive, shut down, remove the 2nd drive.

If you have a modern enough computer, with a usb port, buy or borrow an external disk "cradle" or "holder". 

Fire up your primary master as usual. Once the desktop is up and operational, attach the usb cable to the broken drive. Power up the 2nd drive. 

Go to:

Places/Computer and see if your drive is listed. Highlight the drive, right click and select mount. Open or browse the drive.

You should see your "old" 

home

folder. Copy it onto your desktop of the primary master and cut and paste from there.

I can't recommend pasting the "old" home over the "new" home. It may take a few minutes to open the "new" home in a file manager window and then to open the "old" home in a separate file manager window, but then you can "select all" in the "old" and COPY (not cut) the files into the "new" home.

---

### Post by devinWhalen on 2008-05-28
thanks for the tips, hope this works.

---

### Post by aysiu on 2008-05-28
When you say *fail*, do you mean the drive won't spin at all?

---

### Post by devinWhalen on 2008-05-28
Yeah, I don't know exactly.  It seems like a power issue to me, like it tries to boot up but just can't.

Setting it up as a slave is my last ditch attempt to get the data off it, I realize that it may not work.  I am just desperate to get the data off.  It has been a few months since my last backup.

---

### Post by aysiu on 2008-05-28
If not, you might want to look into *dd_rescue*

---

### Post by devinWhalen on 2008-06-02
Setting up the drive as a slave worked like a charm, I was able to get all my data off it.  

If anyone else has a harddrive die just give this a shot, it was really easy.

Thanks for the help.

---

