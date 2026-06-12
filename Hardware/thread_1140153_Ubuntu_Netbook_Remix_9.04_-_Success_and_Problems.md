---
title: "Ubuntu Netbook Remix 9.04 - Success and Problems"
date: 2009-04-27
forum: Hardware
---

### Post by linuxone on 2009-04-27
Hi,

of course I installed UNR 9.04 on my brand new Asus Eee PC 1000HE beside the already existing and for some reasons (unfortunately) still needed Windows XP partition.

First the good news: Netbook Remix 9.04 could be installed and is running without problems. WiFi network, WPA2 protected, could be used inside the Live System and into the installed system. Basicly all could be fine, but ...

Unfortunately there are a few serious problems with Ubuntu Netbook Remix 9.04:

No root disc encryption available during installation. Root encryption is absolutly required for these small mobile Atom computers, OF COURSE!

Furthermore the Linux Boot Manager is installed without any question ... into the hard disc MBR. Great. :( :confused: 
No matter sda1 does contain a TrueCrypt encrypted Windows XP system. No matter the MBR does already contain a TrueCrypt Boot Loader. No choice to select another place for grub. Real bad.

Thomas

---

### Post by snowpine on 2009-04-27
Use the Alternate Install CD, it has more options (including encryption). Do a CLI (command line only) install, and then 'sudo apt-get install ubuntu-netbook-remix'.

---

### Post by sgosnell on 2009-04-27
The grub bootloader goes where you tell it to go, but the option to put it anyplace other than (hd0) is obscure.  At the penultimate screen, just before you click the final install button, click on the Advanced button.  That gives you the option to install the bootloader elsewhere.

---

### Post by linuxone on 2009-04-28
> **snowpine said:**
> Use the Alternate Install CD, it has more options (including encryption). Do a CLI (command line only) install, and then 'sudo apt-get install ubuntu-netbook-remix'.

thanks - that's what I planned to do.

I opened this thread because I couldn't find any notice about these missing feature(s) and IMO it's an important point.

Thomas

---

### Post by linuxone on 2009-04-28
> **sgosnell said:**
> The grub bootloader goes where you tell it to go, but the option to put it anyplace other than (hd0) is obscure.  At the penultimate screen, just before you click the final install button, click on the Advanced button.  That gives you the option to install the bootloader elsewhere.

I really missed this button. :(  Maybe because I selected install from boot screen and expected to get the well known text install but got an graphical installer?
I'll retry and check the installation into a Virtual Machine on my desktop by time, but first I need to get my Asus Eee installed for work with an encrypted root.

Thanks.
Thomas

---

### Post by sgosnell on 2009-04-30
Why do you need the root files encrypted?  They're pretty generic in most cases.  I understand the need for having the home folder and any other data files encrypted, but not root.  What am I missing?

---

### Post by linuxone on 2009-04-30
> **sgosnell said:**
> Why do you need the root files encrypted?  They're pretty generic in most cases.  I understand the need for having the home folder and any other data files encrypted, but not root.  What am I missing?

Why not? Why should I work with encrypted directories and always remember this restriction during my daily work, for example when storing a configuration with passwords in /etc and so on?
IMO all mobile computers, specially Netbooks, should have root disk encryption. Not partially encrytion but encryption of the whole disk.

Furthermore I do store private and office documents and applications and my development environment on my mobile Computer. To be able to do this root disk encrytion is required to protect all this. Without I won't get permission to store office documents in the netbook.

Thomas

---

### Post by sgosnell on 2009-05-01
Storing passwords in /etc, unencrypted?  What is doing that?  

If you want the entire disk encrypted, there are certainly methods available to do that.

---

### Post by linuxone on 2009-05-01
> **sgosnell said:**
> If you want the entire disk encrypted, there are certainly methods available to do that.

It's already done, using a bootable USB memory stick containing Jaunty 9.04 alternate. After installation of the Netbook Remix package everything is fine and my Asus 1000HE Netbook is running perfectly. :)

Thomas

---

