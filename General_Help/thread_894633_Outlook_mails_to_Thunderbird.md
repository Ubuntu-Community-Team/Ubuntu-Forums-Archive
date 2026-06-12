---
title: "Outlook mails to Thunderbird?"
date: 2008-08-19
forum: General Help
---

### Post by FHS_ on 2008-08-19
Hi there,
I'm a new user of Ubuntu (installed it yesterday) and I was wondering how you transfer mails from Outlook to Thunderbird?
Before I installed Ubuntu, I moved all my files on my computer (including outlooks *.pst) to an extern hard drive.

And the only "tutorials" I can find regarding this, is if you still have Windows on your computer, which I don't.

How can I move the mails without having to install Windows (I don't have the CD)?

Thanks in advance!

---

### Post by Cheesehead on 2008-08-19
It can be done, welcome to the deep end of the pool.

You need to convert your current .pst file to an mbox file, readable by Thunderbird or Evolution. 'readpst' worked for me in the distant past.

1) Get 'readpst' from Synaptic, or from the command line:
```
sudo apt-get install readpst
```

2) Copy your .pst file onto your Desktop

3) Use readpst to convert the file. On the command line:
```
readpst -r Desktop/NAME.pst
```

4) Copy the contents of the converted mbox files into the appropriate folders in your .thunderbird/mail folder.

5) Quit and restart Thunderbird (not the whole computer).

Naturally, it won't be just that easy. Commands won't work, strange errors will pop up, etc. I've seen rumor that readpst can't read Outlook 2007 pst files, for example.

So when you hit a problem, be as specific as you can: My pst was created by Outlook 20__, my error message said "xxx" when I used command "yyy". You can also try Googling the error message or command or symptom - someone else may have posted a solution somewhere else...

---

### Post by FHS_ on 2008-08-19
Thanks a lot! I'll give it a shot and write here when I get it to work or not. :)

---

### Post by FHS_ on 2008-08-19
```
karrow@Karrow:~$ readpst -r Desktop/Outlook.pst
Opening PST file and indexes...
debug_fp is NULL
cannot open PST file. Error
debug_fp is NULL
Error opening File
karrow@Karrow:~$ 
```

That's what it said when I used the readpst -r Desktop/Outlook.pst once I transfered the *.pst file to the desktop...
The *.pst file was made in Outlook Express 2003.

---

### Post by gaussian on 2008-08-19
I know this is very low tech way of doing this, but I did this long time ago (2003ish):copy your mail in batches to an email server (POP/IMAP) using Outlook and download them to Thunderbird. Not very elegant, but can be very doable depending on the amount of mail.

Oops: Just reread the original post (about not having access to Windows). Just ignore this.

---

### Post by FHS_ on 2008-08-19
> **gaussian said:**
> I know this is very low tech way of doing this, but I did this long time ago (2003ish):copy your mail in batches to an email server (POP/IMAP) using Outlook and download them to Thunderbird. Not very elegant, but can be very doable depending on the amount of mail.

Don't I need XP for this? I don't have it anymore...or can I use Wine and download Outlook or something? I'm a bit confused. :P

---

### Post by gaussian on 2008-08-19
> **FHS_ said:**
> Don't I need XP for this? I don't have it anymore...or can I use Wine and download Outlook or something? I'm a bit confused. :P

It was my bad. Yes you would need Outlook and XP for this. You could try to run Outlook under Wine, I have never done it. One thing you could try is to download Eudora and run that under Wine. Eudora 7.1 seemed to install and run nicely under Wine here. It supposedly has Outlook import (I don't have any .pst files, so I can't try). If you get mail to Eudora from there to Thunderbird should be doable with Googling.

---

### Post by Cheesehead on 2008-08-19
Unfortunately, you are right: readpst cannot handle Outlook 2003 .pst files.

So, here are your two viable options. Unfortunately both require a Windows machine (perhaps a coworker or friend?) for a few minutes.

Option 1) Install Thunderbird on the Windows machine, import the .pst file(s), then export the mbox files for transfer to the Ubuntu machine.

Option 2) Open the .pst files in Outlook, and save them again as Outlook 97 .pst files that readpst can handle.

Honestly, poking about any more looking for a linux-based solution is a waste of your time.


** Evolution & Thunderbird should have this ability already...but don't. **
Support Brainstorm Idea #11314 - Migrating My E-Mail Should Be Easy
[http://brainstorm.ubuntu.com/idea/11314/](http://brainstorm.ubuntu.com/idea/11314/)

---

### Post by FHS_ on 2008-08-19
Oh..okay. I'll see if I can fix it tomorrow then (it's 10pm here in Sweden) and I'll get back to you if it worked or not.

Thank you for your answer! :)

---

### Post by FHS_ on 2008-08-20
How do I transfer the mails from Thunderbird on the XP computer to Thunderbird on the Ubuntu computer?

I have now downloaded Thunderbird on a XP computer, imported the *.pst file to Outlook and then imported it to Thunderbird.
What next?

---

### Post by gaussian on 2008-08-20
> **FHS_ said:**
> How do I transfer the mails from Thunderbird on the XP computer to Thunderbird on the Ubuntu computer?

I have now downloaded Thunderbird on a XP computer, imported the *.pst file to Outlook and then imported it to Thunderbird.
What next?

I assume they are in your XP computer's Thunderbird's "Local Folders". 

1) In XP's Thunderbird "Compact Folders"
2) Search for the location of the mails in XP on the harddrive (Somewhere under "Users and Settings", haven't really used windows for years). You should look for your Thunderbird profile, I am sure little googling will tell you standard location for this.
3) Copy those files to a media (whole "Local Folders") tree
4) Copy the files to your Ubuntu Thunderbird folder under local folders (something like /home/username/.mozilla-thunderbird/894320fdslk(random characters)/Mail/Local Folders)
5) Start Linux Thunderbird

---

### Post by FHS_ on 2008-08-20
Thank you very much! :D
It finally worked! Thank you.

---

