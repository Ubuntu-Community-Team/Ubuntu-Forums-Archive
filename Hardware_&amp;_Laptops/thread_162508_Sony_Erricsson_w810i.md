---
title: "Sony Erricsson w810i"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by Cl1maX on 2006-04-19
Is there anyway to mount this in Ubuntu so i can copy stuff to and from the phone via the usbcable?

I havent got a bluetooth hub yet.  I presume it works but would also like the option of using it via the included usb disk.  Atm ui have to use my gf's doze laptop:s

cheers :)

---

### Post by apanloco on 2006-05-05
I'm also interested in this. I guess you could use the provided memory-card converter and use it in a 7-in-1 card reader (i know nothing about that, but I guess it would fit in one!! :).

Or bluetooth, yeah, I'll try that now.

/D

---

### Post by apanloco on 2006-05-05
I just got it working with bluetooth. I am using the KDE desktop. At first I couldn't get it authenticating. The phone requires a PIN code, and KDE never asked me. I had to edit the file /etc/bluetooth/hcid.conf, and change "security" to "user", and "pin_helper" to "/usr/lib/kdebluetooth/kbluepin;".

Thats it, enjoy.

/D

---

### Post by jjeremia on 2006-05-05
[QUOTE=Cl1maX]Is there anyway to mount this in Ubuntu so i can copy stuff to and from the phone via the usbcable?

I havent got a bluetooth hub yet.  I presume it works but would also like the option of using it via the included usb disk.  Atm ui have to use my gf's doze laptop:s

cheers :)[/QUOTE]

When I first connected my W810i, Nautilus showed me the file structure of the phone. But after that I did not succed to connect again....
I have the Logitech Novo Bluetooth, but there is at the moment no support for this as a blutooth hub for now...???

Joakim

---

### Post by Cl1maX on 2006-05-06
[QUOTE=jjeremia]When I first connected my W810i, Nautilus showed me the file structure of the phone. But after that I did not succed to connect again....
I have the Logitech Novo Bluetooth, but there is at the moment no support for this as a blutooth hub for now...???

Joakim[/QUOTE]


Weird it hasnt even tried on my phone :s

---

### Post by Cl1maX on 2006-05-06
[QUOTE=apanloco]I just got it working with bluetooth. I am using the KDE desktop. At first I couldn't get it authenticating. The phone requires a PIN code, and KDE never asked me. I had to edit the file /etc/bluetooth/hcid.conf, and change "security" to "user", and "pin_helper" to "/usr/lib/kdebluetooth/kbluepin;".

Thats it, enjoy.

/D[/QUOTE]


What bluetooth hub are you using in linux ?

---

### Post by apanloco on 2006-05-25
I'm using a mac mini. Don't know what comes with it...
Sorry for the late reply.
/D

---

### Post by LetsLinux on 2006-10-20
I got my w810i yesterday - and I instantly plugged it into my Kubuntu via the USB-cable and it worked. 

On the phone I selected "File Transfer" and after a few seconds two icons on the desktop entitled "Phone" and "Phone Card" appeared - and I was on the run. (I figured out that sometimes it takes up to 30 seconds for Linux to notice the phone)

Afterwards I've restarted the machine several times - and it automatically mounts the whone whenever I plug it it.

However, if anyone know of an application where you can send and receive SMS messages via Bluetooth - then please let me know! 8) 

Jonas

---

### Post by Jagunço on 2007-08-18
Hi people!

When I plugged my SE W810i for the first time in my Ubuntu laptop (a few months ago), the system recognized 'USB Phone' and 'USB Phone Card' and everything worked Ok.
Now, when I plug the W810i, the system only recognizes 'USB Phone Card' and every file transfer ends up with an error.
What's going on?

TIA.

---

### Post by Dark Star on 2007-08-18
Have you tried via USB drive . .MY K810i easily get mounted :D

---

### Post by Jagunço on 2007-08-18
> **Dark Star said:**
> Have you tried via USB drive . .MY K810i easily get mounted :D

I didn't understand, sorry... what do you mean with USB drive?
When I plug the USB cable and set the phone to 'File transfer', the system only recognizes the phone's memory card and every transfer fails.
If I set the phone to 'Phone mode', the system doesn't even recognize the phone.

---

### Post by tgalati4 on 2007-08-18
>dmesg

Look for errors.  It could be that your card is corrupted or not clean so it won't automount.

Try:

fsck /dev/sda2

(Your device designation may be different.)

---

### Post by Jagunço on 2007-08-18
> **tgalati4 said:**
> >dmesg

Look for errors.  It could be that your card is corrupted or not clean so it won't automount.

Try:

fsck /dev/sda2

(Your device designation may be different.)

Thanks, I'll try this.

But everything is working just fine on my Windows box, so I think my card is ok.

---

### Post by prabath_fun on 2008-07-22
Hi,
   Any one connected SE W810I under phone mode to transfer files from and to PC through USB cable? i.e., like PC Suite. 

Please describe.

I am using Ubuntu 8.04.

Prabath

---

### Post by bellmount on 2008-07-23
Hi,
plug your USB cable into your PC, then the other end into your phone.
The phone will give you a beep ask which mode it should operate in. For file transfer it needs (!) to be in file transfer mode. So select that and wait for Ubuntu to mount (if you have disabled automatic mounting, you'll have to do it manually) first your phone and, if you have one, your phone card.

This may take a little while, your phone screen will go blank, then blink, show the black SE screen, then tell you it is preparing file transfer and at last have an orange screen with a message telling you to NOT remove the USB cable. Now you should find icons on your computer's desktop for both "phone" and "phone card" and can easily transfer files in your file manager.

I use my W810i on all sorts of computers  (instead of an USBstick or burning CDs all the time) and never had to install any drivers or software.
The one important thing is to unmount (from the context menu) first the card, then the phone before you remove the cable and give the little friend some time to find itself afterwards. 

Have a nice day,
bellmount

---

### Post by prabath_fun on 2008-07-24
Hi Guys,
   I am looking for "phone Mode" operation, **[SIZE="3"]not[/SIZE]** "File transfer" Mode operation.
   I tried with Gnome phone Manager with various ports. It is not detecting my phone. Anyone if got, please update me how to do?

With Thanks,
Prabath

---

