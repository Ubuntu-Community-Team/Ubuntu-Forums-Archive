---
title: "Ubuntu won't install on ASUS notebook"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Joakal on 2009-02-02
I currently have a CD with Ubuntu 8.10 as an .iso. Search results yield nothing specific besides [this](http://ubuntuforums.org/showthread.php?t=422950) and google results had some technical jargon ([this](https://answers.launchpad.net/ubuntu/+question/37991)).

Hardware manufacturer and computer code(?): 
ASUSTek Computer Inc. F3JV

Problem solving attempts:
[list][*]CD/DVD was not burned properly; I have confirmed the CD is an .so. It even auto-runs in Windows.
[*]BIOS; I don't appear to have a BIOS. It flashes ASUS and then goes straight to windows loading message.
[*]PC requires you to hold down or press a key to boot from CD; I tried to press tab, got barely one second view before it went straight to windows. Didn't work for F12 either.
[*]Multiple CD/DVD drives in your computer; I only have one DVD player
[*]SmartBootManager; Seems to require a floppy disk which I don't have.[/list]

My only option to install is from auto-run or **Install inside Windows**.

Thanks for any help

---

### Post by Mouth on 2009-02-02
When you look at the contents of the CD, do you see just one file (The *.iso file), or do you see many files.

If you only see the 1/one *.iso file then you haven't burnt it correctly.

---

### Post by Joakal on 2009-02-02
I see many files as soon I open the DVD drive.

---

### Post by Joakal on 2009-02-02
I burnt a disc using Alternative CD or ubuntu-8.10-alternate-i386.iso

Initially it didn't work much like the previous CD.

However I remembered and since there was a very brief appearance upon pressing "Tab" key, I tried the "Pause" key. It worked and gave me two options, F2 to enter setup or Esc. Pressing F2 once didn't do it so I was pressing F2 multiple times to be able to get into the BIOS screen. From there, I went drives set up and chose the different order to load, eg:

Removable Storage
Hard Drive
CD/DVD drive
Something (Forgotten)

to

CD/DVD Drive
Removable Storage
Hard Drive
Something

Then chose the key to Save and Exit.

Shortly entered Ubuntu screen after some CD and RAM tests.

---

