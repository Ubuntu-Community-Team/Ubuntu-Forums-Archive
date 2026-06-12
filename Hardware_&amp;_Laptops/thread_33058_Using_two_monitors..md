---
title: "Using two monitors."
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by Michael Treadgold on 2005-05-09
I am new to Linux, and Kubuntu is my first since the Evil Wxndxxs.

I am pleased to announce I am very happy with most things here, I cannot use my dual head ATI 9600XT. This was a simple matter in XP but here I have no idea where video drivers are configures.

Can anyone give me some pointers? I just want to spread my desktop over two monitors. I am an Audio engineer and have used computers since PCDOS.

Any help would be gratefully accepted.

Thanks in advance.

Mike, London

---

### Post by davidmigl on 2005-05-31
Please, could someone help us out?  I have the same exact card and want to do the same exact thing!

---

### Post by Leif on 2005-05-31
Please search the forums for twinvew, and see which thread has info on a system closest to yours.

---

### Post by shakin on 2005-05-31
First, install the real ATI driver from the repository.

```

$ sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx

```

Now make a backup of your /etc/X11/xorg.conf file (just in case something goes wrong you can boot to console and replace the new one with this backup).

Run 'fglrxconfig' and the ATI configuration program will allow you to select various things about your driver setup, including which multi-desktop type to run: dual head is a bit odd in that you can't drag back and forth between monitors, but it operates more like two completely separate computers. Big desktop is what Windows does. Select whichever you want.

When running fglrxconfig if you have any trouble answering the questions, you can refer to your backup xorg.conf file. You may need this for things like monitor refresh rates.

---

### Post by codemills on 2005-06-02
[QUOTE=shakin]First, install the real ATI driver from the repository.

```

$ sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx

```

Now make a backup of your /etc/X11/xorg.conf file (just in case something goes wrong you can boot to console and replace the new one with this backup).

Run 'fglrxconfig' and the ATI configuration program will allow you to select various things about your driver setup, including which multi-desktop type to run: dual head is a bit odd in that you can't drag back and forth between monitors, but it operates more like two completely separate computers. Big desktop is what Windows does. Select whichever you want.

When running fglrxconfig if you have any trouble answering the questions, you can refer to your backup xorg.conf file. You may need this for things like monitor refresh rates.[/QUOTE]
 umm has the thread starter able to get it running by the provided solution?

i have ati 9600 *lowers voice* SE card.... and dual thing works in windows easily (saying this to tell nothing wrong with card)

so now how to set dual thingy here?

---

