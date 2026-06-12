---
title: "Drivers for Generic SoftK56 modem?"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by ultima2k on 2005-04-22
Well it's like this that I got an internal modem called "Generic SoftK56" and if I try creating a connection and find which port it uses, it won't find anything. Hade also tryed manually choose port and connect, but nothing happends. The modem isn't broken because it works in Windows.
Do I need to install som linux drivers to make it work, and if yes, where can I find it(have searched, but found nothing)

I really want to be able to connect so that I can install XMMS, MPLAYER and much more :(

---

### Post by cowbud on 2005-04-22
Your best bet is to check out the linuxant software modem drivers: 

[http://www.linuxant.com](http://www.linuxant.com) 

They have a few scripts to test which modem you have but you do have to pay if you want to use the modem faster than 14.4 :(

---

### Post by ultima2k on 2005-04-22
Pay?

Damn that's so sucky!

---

### Post by az on 2005-04-22
A lucent or Intel based software modem is cheaper.  You can get then new on ebay for less than 10 USD.

---

### Post by ultima2k on 2005-04-22
I don't really get this, what's a software-modem?
And I have a lucent-modem, but it's broken, won't go faster than 30kbps in windows(didn't work in ubuntu either)

---

### Post by az on 2005-04-22
[QUOTE=ultima2k]I don't really get this, what's a software-modem?
And I have a lucent-modem, but it's broken, won't go faster than 30kbps in windows(didn't work in ubuntu either)[/QUOTE]


I *hate* editing other people's posts.  Please do not use offensive language in the forums.

A modem turns sound into data.  It can do this all by itself, using it's own technology, or by using your cpu to decompress and decipher the data.  A hardware modem does all that by itself.  A hardware modem is more expensive than a software modem.

A software modem basically hooks the phone line to the software driver which uses you cpu to do all the work.  This usually chews up something like 300 to 400 mHz of cpu power.

A software modem (softmodem, windmodem or linmodem - different names for the same thing) if really cheap since it does not contain a lot of technology.  They are driver dependant so if the company does not make a driver for linux, it will not work.
Lucent and intel have proprietary drivers available for free.  Intel's (smartlink use intel chips) driver is moving towards phasing out the proprietairy driver in favor of an open source one (actually, the alsa sound system modem driver).

If you are a free software proponent lke me, and use open source sofware because of the freedom you get, this is good.  Perhaps Lucent and the other companies will follow.

Conexant have another business model.  They sell you the driver.  You get support for about a year, which means that if you want to use a different kernel in a year, you may not be able to continue using the old driver and may have to buy it all over again.  They sell it fo 14.99 US Dollars.

Since technology companies are somewhat volatile, these things can change at any time, though.

Your modem sounds broken.  Do you have a clear phone line?  Do other modems work well?

---

### Post by ultima2k on 2005-04-23
Mkay...then I know what a software-modem is :)
But how can the sound of the modem be broken if it works in windows(yeah, it's not linux I know, but it works)?

And what offensive language did I use?

EDIT: so there should be linux drivers for lucent-modems to download?
Then I'm gonna search some for it, my crappy lucent modem(aka max 30kbps) is better then nothing :p

---

### Post by az on 2005-04-23
"Mkay...then I know what a software-modem is
But how can the sound of the modem be broken if it works in windows(yeah, it's not linux I know, but it works)?"
What do you mean by this and which modem are to talking about?

"And what offensive language did I use?"

You did not say "broken"

"EDIT: so there should be linux drivers for lucent-modems to download?
Then I'm gonna search some for it, my crappy lucent modem(aka max 30kbps) is better then nothing "

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

### Post by ultima2k on 2005-04-23
Hehe, just mean that the modem won't go faster than 30Kbps which I think it has done before. Anyway the modem works even if it slow like h**l.

Thanks for the link to your guide, hope it works :)

EDIT: just to make you know, I'm from sweden so the writings can go pretty weird sometimes :p

---

### Post by ultima2k on 2005-04-23
Now I have used the modem-scan and I have a lt-lucent modem.
Because I'm a linux newbie those steps you quoted are not easy to understand.

Is the "restricted-modules" already included in Hoary?
Wtah do you mean by "put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot."

Thanks so far :)

---

### Post by az on 2005-04-23
"Is the "restricted-modules" already included in Hoary?"

Yes.  Warty also has a linux-restricted-modules package, but it does not include the ltmodem drivers.

"Wtah do you mean by "put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot."

/etc/modules is a file.  It is parsed (read) at boot time and all the modules that are named in it are loaded.

Add "lt_serial" and "lt-modem" to the list.  You need to edit the file using sudo, since it is a file owned by root.  

sudo gedit
or use a terminal and do
sudo nano /etc/modules
(CTRL-O to save and CTRL-X to exit nano)

---

