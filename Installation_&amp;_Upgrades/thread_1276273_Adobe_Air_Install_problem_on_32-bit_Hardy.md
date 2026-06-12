---
title: "Adobe Air Install problem on 32-bit Hardy"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by GaryUK on 2009-09-26
I run a dual boot XP/Hardy installation on a Dell 8400 P4-3.4Ghz with 400Gb HDD. Up until Recently I had Spaz working on Adobe Air but I trashed it and Adobe Air in order to remove all Adobe products before re-installing Flash to make Firefox see the upgrade to Flash 10.

I now find that I cannot get the Adobe Air installer bin file to execute. I have re-downloaded several times and then run:

```
sudo chmod 777 AdobeAIRInstaller.bin
```

And my bin file looks like this:

> garyd@Home:~/downloads$ ls -al Adobe*.*
-rwxrwxrwx 1 garyd garyd 13745012 2009-09-27 01:14 AdobeAIRInstaller.bin


After I issue the following command in the downloads directory:

```
./AdobeAIRInstaller.bin
```

And then nothing happens and the Air Installer does not start.

Anyone any clues as I really want to get Tweetdeck working in Ubuntu.

Thanks in advance for any assistance you can give!!

:confused::confused:

---

### Post by rreese6 on 2009-09-26
did you try ```
sh  AdobeAIRInstaller.bin
```

---

### Post by GaryUK on 2009-09-27
> **rreese6 said:**
> did you try ```
sh  AdobeAIRInstaller.bin
```

No, but I have now and this is what I get - looks to me like a problem with the Adobe bin file??

> garyd@Home:~/downloads$ ls -al Adobe*.*
-rwxrwxrwx 1 garyd garyd 13745012 2009-09-27 01:14 AdobeAIRInstaller.bin
garyd@Home:~/downloads$ sh AdobeAIRInstaller.bin
AdobeAIRInstaller.bin: 1: Syntax error: "(" unexpected


As always, any suggestions will be much appreciated.

Thanks in advance for your help!!

#-o

---

### Post by rreese6 on 2009-09-28
Evidently Adobe has chosen to require that you use root to install it
I don't like that idea, but they say that the widget only have user permissions...
ok so if you decide you really trust Adobe and you actually downloaded the file from them,
then do:
```
sudo chmod +x AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
```

one other note, be very careful about using chmod 777....that can be real dangerous cause it gives everyone access to the file.

---

### Post by GaryUK on 2009-09-29
> **rreese6 said:**
> Evidently Adobe has chosen to require that you use root to install it
I don't like that idea, but they say that the widget only have user permissions...
ok so if you decide you really trust Adobe and you actually downloaded the file from them,
then do:
```
sudo chmod +x AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
```

one other note, be very careful about using chmod 777....that can be real dangerous cause it gives everyone access to the file.

Thanks my friend but I already know the dangers of chmod and your +x is really like doing a chmod 755 (filename) - I use the chmod number as, since I have been consulting on Unix systems for 15 years, I know it works on all flavours. Sorry, don't want to sound ungrateful but very late here and I genuinely do take the point.

I already tried to use sudo and that does not work.

I genuinely think the bin file is busted - I did not have this problem when I installed Air the first time around and nothing much has changed on my Linux set-up since.

Has anyone managed to install Adobe Air 1.5.2 ??

:frown: :frown:

---

### Post by geekosupremo on 2009-09-30
GaryUK, I used rreese6's instructions and it seemed to work fine for me. Now have Twhirl working. 

Oh ... I'm using Jaunty ... so that maybe why it worked. Not positive, since I'm an Ubuntu/linux Newb.

---

### Post by GaryUK on 2009-10-07
> **geekosupremo said:**
> GaryUK, I used rreese6's instructions and it seemed to work fine for me. Now have Twhirl working. 

Oh ... I'm using Jaunty ... so that maybe why it worked. Not positive, since I'm an Ubuntu/linux Newb.

Hey geekosupremo, tried to download and install Air again using rreese6's instructions to the letter - No Dice, so it would seem making bin file executable for root and then doing an execution of the bin file as root may work for jaunty but not for Hardy 8.04.3 LTS.

Anyone at all managed an install of Air 1.5.2 and Tweetdeck on Hardy??

Thanks to all for your help!!:confused:

---

### Post by GaryUK on 2010-02-13
Sorry that this is a very belated update - Adobe Air now seems to be working on Hardy. Did not do anything that I can put my finger on to get it to work. I now have the delights of Tweetdeck on Linux Woo Hoo !!:)

---

