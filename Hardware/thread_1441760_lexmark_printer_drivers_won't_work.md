---
title: "lexmark printer drivers won't work"
date: 2010-03-29
forum: Hardware
---

### Post by elite0083 on 2010-03-29
they have drivers for linux on the official lexmark site, but they only have debian and redhat based and since ubuntu is debian based I thought it would work, but when I go to install it gedit says..... (gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.) 

thanks in advance,
Elite0083:-k

---

### Post by ajgreeny on 2010-03-29
Why are you using gedit to install a printer driver?  I have not used a Lexmark printer in ubuntu at all, so have no idea what the driver is or requires of you, but gedit seems an unusual way to install anything; it's a text editor.  What exactly is the diver file, and how are you trying to install it?

For future reference, I would suggest you avoid Lexmark for use with ubuntu, or any other linux distros, as they are fairly well known for being best as paperweights, not much good as linux printers, though I am sure there will be some who say their machine has worked well.  Generally HP and Epson are good, Brother is getting much better, and their printers and MFCs are really good, but I can't really comment on other makes, as I have no experience of them.

---

### Post by coffeecat on 2010-03-29
Are you double-clicking on the downloaded .deb file and it's trying to open in gedit? If so, something's gone wrong with your filetype associations. Post details and we'll help you fix that. Also, please post details of your Lexmark printer model. With that we can check the OpenPrinting site. There may be better ways described there of getting your Lexmark to work - hopefully.

---

### Post by elite0083 on 2010-09-02
I apologize for taking so long I have been away on business, I tried downloading the .deb file and running it, but it says its the wrong architecture. it is a lexmark x7675

---

### Post by coffeecat on 2010-09-02
Wrong architecture means you have downloaded a deb file for a 64-bit system and are trying to install it on a 32-bit system, or vice versa. If you post the link from where you got the driver, which version of Ubuntu you are using and whether it's 32 or 64 bit, we'll be able to help you.

---

### Post by elite0083 on 2010-09-05
I downloaded the ones off this page [http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X7675&page=recommendedDownloads#2](http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X7675&page=recommendedDownloads#2)  under where it says linux and the one that says Debian, i am running ubuntu 10.04 in a 32 bit architecture.

---

### Post by coffeecat on 2010-09-05
> **elite0083 said:**
> I downloaded the ones off this page [http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X7675&page=recommendedDownloads#2](http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X7675&page=recommendedDownloads#2)  under where it says linux and the one that says Debian, i am running ubuntu 10.04 in a 32 bit architecture.

Well, that's odd because the Debian package is called lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz, which would be a 32-bit package. My main Ubuntu 10.04 installations are all 64-bit so I can't check that file on those, but I have installed the netbook version of Maverick Beta on my netbook (which is 32-bit). I'll try downloading and running that file on the netbook and see what happens. I'll get back.

---

### Post by coffeecat on 2010-09-05
How did you try running the file? As I couldn't find any instructions on the Lexmark site, after  downloading the lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz file to my netbook, I extracted it, opened a terminal and cd-ed to the Download folder, and then:

```
sudo bash lexmark*sh
```That seemed to start it off OK, a Lexmark GUI wizard opened, I clicked on next and then the terminal promptly crashed. Of course, this is in Maverick Beta, so don't read too much into the crash. I think there is a bug in sudo at the moment. Anyway - I didn't see a wrong architecture error message.

If that was not the way you tried to run it, give it a whirl and see what happens.

---

### Post by elite0083 on 2010-09-06
this is the first time its every worked like this. Ok so I was trying to install it, but it kept asking for a root password which i didn't have so i did the research online and changed the root password and from there i installed it, only problem is I can only use the print function (no scanner, wireless, etc)

---

### Post by coffeecat on 2010-09-06
> **elite0083 said:**
> Ok so I was trying to install it, but it kept asking for a root password which i didn't have so i did the research online and changed the root password and from there i installed it,

That's why you need to do 'sudo bash' in Ubuntu. Normally the root account is locked in Ubuntu, but the first created user has full administrative powers with their own password. It's very remiss of Lexmark not to include installation instructions on their website, or a readme in the package - many users would not know this.

With regard to root and sudo, you might find this a useful read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

>  only problem is I can only use the print function (no scanner, wireless, etc)I guess that's only a printer driver. You might want to search the Lexmark site again for a scanner driver but it might be a lost cause - sorry. Lexmark used to have a reputation for being very unsupportive of Linux and you'll find plenty of threads here recommending people not to get Lexmark. To be fair to Lexmark, they've recently had some sort of epiphany and are getting more interested in Linux support but, clearly, there must be a big backlog of older models to cover - and which may never get Linux drivers. Even Hewlett-Packard, which is the most Linux friendly printer manufacturer produces printers that will not work in Linux.

---

