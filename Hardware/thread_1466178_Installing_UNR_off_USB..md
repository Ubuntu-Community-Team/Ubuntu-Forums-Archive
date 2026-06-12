---
title: "Installing UNR off USB."
date: 2010-04-30
forum: Hardware
---

### Post by Qwerty_ on 2010-04-30
I am having some problems installing 10.04 netbook remix off of a USB onto my Acer Aspire One netbook.

Firstly the USB-Creator.exe was not accepting the .iso as an image to create the bootable USB, so I proceeded to use the UNetbootin USB creator, that worked fine. However, now when I try to boot off of the USB it seems to hang after I select to use Default.

Any ideas? I have downloaded the netbook remix this morning and the MD5 sums are correct.

---

### Post by wilee-nilee on 2010-04-30
> **Qwerty_ said:**
> I am having some problems installing 10.04 netbook remix off of a USB onto my Acer Aspire One netbook.

Firstly the USB-Creator.exe was not accepting the .iso as an image to create the bootable USB, so I proceeded to use the UNetbootin USB creator, that worked fine. However, now when I try to boot off of the USB it seems to hang after I select to use Default.

Any ideas? I have downloaded the netbook remix this morning and the MD5 sums are correct.

Are you sure it is a ISO in the past there have been images for the UNR, post your download link. This is a strange thing as well USB-Creator.exe  .exe is windows.

---

### Post by Qwerty_ on 2010-04-30
Yes it is an ISO I downloaded it from [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
And downloaded the [http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso) file.

I was running USB-Creator in XP and it runs but when I select the netbook iso it does not go into the list at the top, this is happening with both XP and Vista.

---

### Post by wilee-nilee on 2010-04-30
> **Qwerty_ said:**
> Yes it is an ISO I downloaded it from [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
And downloaded the [http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso) file.

I was running USB-Creator in XP and it runs but when I select the netbook iso it does not go into the list at the top, this is happening with both XP and Vista.

Since you have not installed yet, if it was me I would reload the thumb with unetbootin, but I suspect that the UNR is lagging in development. You could download a standard i386 and see if it runs live. personally I have found the UNR to be problematic. With this being the 2nd day of release The downloads could be corrupt even if the md5 says it is correct anything is possible. Sorry I don't have a more definitive answer.

---

### Post by Qwerty_ on 2010-04-30
I might try another thumb drive because it's a pretty slow one ive been using. Thanks for your help perhaps giving it a few days might be a good idea.

EDIT:
I have re made a bootable SD card this time. Whilst creating the SD card it seems to pause at 4$% for some time.

Re-creating the bootable card has not made any difference as it has come to a hault on the UnetBootin startup screen.

---

### Post by Qwerty_ on 2010-05-03
Just an update, I had to redownload the iso via bit torrent, the USB-Creator was still not recognising the iso however Unetbootin did and I was able to create a working USB that booted up.

It just seems odd that the USB creator tool was not working when it came from the ISO it's self. (And yes I had extracted it and ran the USB-Creator program with nothing else using the iso)

---

