---
title: "i try to install downloaded things but it keeps erroring:p please help me someone"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by h33d sight3d on 2008-12-21
please help me someone..
im trying to download a pokemon game but when i go to install it does this.
----------------------------------------------------------------------------
caution: filename not matched:  Pokemon Crystal (F) [C][!].gbc

1 archive had fatal errors.
----------------------------------------------------------------------------

if someone could tell me how to solve this then i would be extremly gr8ful:P:P:P:P:P:popcorn::guitar::lolflag:

---

### Post by zvacet on 2008-12-21
Did you downloaded file with deb extension (file.deb) or extension is different? What is exact name of file you downloaded?

---

### Post by h33d sight3d on 2008-12-22
it was

Pokemon Crystal (F) [C][!].zip

thats the file name

please help me out

---

### Post by Lacrimstein on 2008-12-22
Hmm looks like this is a gameboy rom? You will need a gameboy emulator for that. I suggest VisualBoyAdvance.
install visualboyadvance like this:
Open Programs->Accessories->Terminal
then type in: 

sudo apt-get install vbaexpress

then enter your password.

The program will be dowloaded and installed.

Afterwards, run vba and launch the game file from there. Hope this helped :KS

---

### Post by h33d sight3d on 2008-12-22
i have done that but when i go to enter my password it wont type anything?
what do you suggest i do.

---

### Post by Lacrimstein on 2008-12-22
The password is not displayed as stars, but it is still entered. Basically you just type it in and press enter

---

### Post by h33d sight3d on 2008-12-22
it still wont work..
when i open the file it just does the same thing as before

any other ideas?

---

### Post by Lacrimstein on 2008-12-22
Oh, you cant unarchive it? Looks like your archive is corrupted. Try getting the game from somewhere else.

---

### Post by h33d sight3d on 2008-12-22
i downloaded from another sourse but the same happens

help?

---

### Post by SlidingHorn on 2008-12-22
> **h33d sight3d said:**
> i downloaded from another sourse but the same happens

help?

Maybe you should...I don't know...**buy** the game?

---

### Post by h33d sight3d on 2008-12-22
why should i buy it when i can get it 4 free

btw
its not the download thats the problem its the fact that i cannot install it

---

### Post by SlidingHorn on 2008-12-22
#1.  Piracy is illegal and not a valid subject to discuss on the forums

#2.  If you're saying that you cannot "execute" the zip file, then yes...it is the download.  Zip files are not installation files - only archives.

From what you've told us, it appears that the ZIP archive you downloaded is corrupted.  If you obtain a working copy, then you would extract the files from the archive to your machine and then run the install file from inside your GameBoy emulator.

If we're wrong, please tell us why so we can get the issue fixed

---

### Post by zvacet on 2008-12-22
I don´t know if any of this will be helpful to you but anyway:

type in terminal

```
sudo apt-get install p7zip p7zip-full
```

after that right click on zip file and see if you can unzip it and then install.

---

