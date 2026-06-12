---
title: "Mail Notification Doesnt Check Mail"
date: 2005-11-15
forum: General Help
---

### Post by Yoda_Oz on 2005-11-15
Hi,
ive got mail notification set up properly as far as i know but it doesnt check my mailboxes, even when i manually click update it doesnt seem to check anything.
the reason i know this is because i will then open up my mail client and it will download 2 or 3 new emails.
do i need to have my mail client open to have mail notification to work? are there any other pop3 mailbox checkers that sit in the panel tray as a standalone program if i cant seem to get mail notification to work?

---

### Post by bionnaki on 2005-11-15
I use mozilla thunderbird & alltray.

---

### Post by Yoda_Oz on 2005-11-15
i'd prefer a standalone program. i dont want to have to minimise a huge resourse eating email client and keep it open all the time in my tray.

if there is no alternative, does alltray show a new mail notification in the tray?

---

### Post by Yoda_Oz on 2005-11-16
ive just discovered when using mail notification that it cannot connect to my email servers for some reason. gkrellm connects fine with its pop checker...

is there something im leaving out in the installation of mail notification?
i have 2 ordinary pop3 inboxes and 1 gmail.

---

### Post by WW on 2005-11-16
It never worked for me either.  It would check the mail when I logged in, but after that, it was useless.  I am now using gnubiff, and it works fine.

---

### Post by Yoda_Oz on 2005-11-16
ive just installed gnubiff. let's see how this one goes...

---

### Post by Yoda_Oz on 2005-11-30
Nope,

I really want to get mail notification to work.
i installed the once on the breezy repo straight from synaptic. is this the right way to install?
anyway, ive set up my 1 pop mailbox in mail-notification but it doesnt check it.

---

### Post by humina on 2005-12-01
I would try the latest version of mail-notification.  The 2.0 version is better.  It is in backports.  I would use the backports server to install the file and then comment it out so that you don't leave your system too unstable.

---

### Post by Yoda_Oz on 2005-12-02
that didnt work.
it just seems like it doesnt check the mail at all..

today i went to click on the mail notification preference in the system menu and it didnt load. i had to kill the process for me to be able to go back in to it.

are there any other programs that sit in the tray monitoring pop3 accounts and alerts when there is new mail?

---

### Post by anil_robo on 2005-12-03
Gdesklets has a little applet for checking pop mail. Try that!

First install gdesklets
```
sudo apt-get install gdesklets
```

Run gdesklets
[menu-->accessories-->gdesklets]
Gdesklets will start as a system tray icon.
Right click on it, choose "manage desklets"
A list of available desklets will appear.
Under the category list, go to the last entry "uncategorized"
On the right hand side, so many desklets will appear.
Choose "popmail display" by double clicking it.
Then simply click on an empty area of desktop to place it.
The desklet will be visible on desktop.
Right click on the desklet, and choose configure
Enter your POP settings
DONE! :)

---

### Post by Yoda_Oz on 2005-12-03
thanks for the reply.
i want a pop checker that sits in the panel or tray. i dont want to have to have a look at my desktop evertime i want to see if ive got mail. i might as well just open up my email client everytime. id like it so that if im running a program and i get email i can see it in the panel or tray, where i dont have to minimise or close anything to check it.

---

### Post by palomar on 2006-03-04
* little kick of this old topic *

I'm also looking for a descent POP3 checker, with notification in the tray. I've tried mail-notification 2.0, but it cannot do something simple like flashing/blinking in the tray, so it's useless for me. Also tried some other mail checkers from tge repositories, but with no luck.

Anyone knows a good POP3 mail checker with notification in the systemtray?

---

### Post by justinjstark on 2006-03-29
I couldn't get mail-notification to work at all until I tried the following .deb.  It's been working fantastic for me with gmail.

[http://wildbill.nulldevice.net/ubuntu/breezy/mail-notification-ssl_2.0-1_i386.deb]("http://wildbill.nulldevice.net/ubuntu/breezy/mail-notification-ssl_2.0-1_i386.deb")

---

