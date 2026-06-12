---
title: "[SOLVED] Problem with Accounts on installation of Wubi"
date: 2008-07-13
forum: General Help
---

### Post by CherryInHove on 2008-07-13
Hi,

I've searched through the first 15 pages of this forum and also read [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and haven't found anyone else who has had this problem, so therefore either it's me being an idiot or just something completely random.

I downloaded and installed wubi and then restarted. Everything seemed to be going OK. Then it got to stage 6 of 7 "Migrate Documents & Settings". This is where it says

"Select any accounts you would like to import. The documents and setting for these accounts will be available after the install completes.

If you do not wish to import any accounts, select nothing and go to the next page".

Now, this is a brand new fresh ubuntu installation. I'm very late to the game I'm afraid, so I don't have an account to transfer across. However, There are two buttons at the bottom, "Cancel" and "Forward". Forward is greyed out and unclickable.

If I selected the only option available which is:

"There were no operating systems suitable for importing from" then the Forward button is still greyed out.

I've tried everything I can do try to be able to click on that forward button, but in the end all I can do is click on "Cancel" which then checks if I want to cancel the installation (which obviously I don't, but have to choose that I do).

Anyway... After I choose to cancel, it the launches ubuntu and everything works. (I even managed to install and run programs). However, when I restart the computer it goes back to exactly the same thing, restarting the installation process and failing at the same spot, and then after choosing cancel again, it doesn't remember anything I've done.

Sorry about the huge amount of text there, but I wanted to try to include everything that I thought might be useful.

If anyone could help me free with this and take a step towards freedom from Microsoft that would be fantastic.

---

### Post by ago on 2008-07-14
Uninstall, reinstall, at reboot press esc and go for verbose mode.

When you get the dialog, press ctrl+alt+f2 and run:

sudo sh /custom-installation/hooks/failure-command.sh

You should find c:/ubuntu/installationlogs.zip

Pls attach it here (note that your password md5 might be included)

---

### Post by CherryInHove on 2008-07-15
Hi,

I went to follow these instructions and this time around it installed perfectly and is now working like a dream (And I'm posting this while using Ubuntu which makes me happy!)

The only things I changed between this install and the one that didn't work is that on the one that didn't work I changed the username from Administrator to Seb, and I changed the storage size to the maximum available. 

This time around I left everything at default and it's all OK. Thanks very much for the instructions though.

---

