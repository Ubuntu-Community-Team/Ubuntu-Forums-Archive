---
title: "Home dir on seperate partition and installing"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by albeano2004 on 2009-05-02
Apologies if something similar has already been posted.
I'm planning on moving my home directory across to a partition on a separate hard drive to the / hard drive. My main concern is that on fresh install of a new release of Ubuntu, that my home dir contents will be overwritten for things like Pidgin. Does anyone here have any experience of what happens on to existing home dir contents on install? Are they left alone? Or do they get overwritten?

Thanks,
Alex

---

### Post by x33a on 2009-05-02
it does preserve your data.

take a look here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by albeano2004 on 2009-05-02
Ah, many thanks. It makes sense for it to preserve data I know, but I'd much prefer to find out this way if it didn't, than the hard way (losing all my data :)).

Thanks again,
Alex

---

### Post by Herman on 2009-05-02
What's going to happen if your /home hard drive has a motor failure or a bearing failure or blows a capacitor on the circuit board then? :confused:

---

### Post by albeano2004 on 2009-05-02
> **Herman said:**
> What's going to happen if your /home hard drive has a motor failure or a bearing failure or blows a capacitor on the circuit board then? :confused:

In that case I'd do exactly what I'd do if I lost any hard drive - buy a new one/get a replacement, then restore from one of my regular backups. Not really an issue imo :)

---

### Post by Herman on 2009-05-02
:) Good, so you're not relying on the fact you will have a separate /home to 'preserve data', that's my point.

---

### Post by albeano2004 on 2009-05-02
> **Herman said:**
> :) Good, so you're not relying on the fact you will have a separate /home to 'preserve data', that's my point.

Ah, gotcha. I've been bitten too many times by failing hard drives, so I know not to make the mistake of having no backups/not enough backups.
My main concern was that if I was to install a fresh copy of Ubuntu, that my /home would be overwritten :).
Hoping to move the / across to a SSD at some point too, when they start coming down in price a little more (still a little too expensive for me :))

---

### Post by Herman on 2009-05-02
Oh I see, in that case I agree with you 100%. I was just concerned for new users who may take what we write literally, so I wanted to clarify that.
I'm excited about SSD drives too, and I'm also looking forward to the day I can get ahold of my first SSD drive.
From what I'm reading, the technology is advancing rapidly, so the question is not only the price, but also whether to buy now or wait a little bit longer for a few more anticipated new features to appear, like firmware support for the ATA trim command, and so on.  :)

---

### Post by Herman on 2009-05-02
And yes, your home directory will be normally overwritten unless you take steps to avoid that, and of course have a backup of your data as well.

**Making a backup** - (just in case there are a few people reading this who don't already know),
It's not very hard or time consuming to make a backup of a few of our most important files and settings. 
What may not be so obvious to a few of those who are new to Ubuntu is that most of our settings for programs we have installed are stored in hidden files and directories in our /home/username folders. 
These files and directories can easily be seen by going to the 'View' menu and clicking 'show hidden files'. These should be included along with regular data in any good backup.

Look especially for .evolution/addressbook .evolution/calendar .evolution/mail .evolution/memos .evolution/tasks. 

Start your firefox web browser and click 'Bookmarks', then 'Manage Bookmarks', then on the 'File Menu' of the 'Bookmarks Manager' window, click 'export'. That will start the 'export wizard'. Give your file a name  that means something to you, or the day's date. Choose a folder to save it in such as /home, and click 'Save'.

There will probably be a few other programs you can backup files and settings for as well. For example, I use 'Password Manager' to keep track of over 50 different accounts and passwords. Some of those are extremely important to me, so of course I always make sure I copy my .gpass directory to any new Ubuntu installation.
Other people will have their own various programs they might need to save the files and settings for. These will obviously vary greatly between one user and another.

**To restore**,
Once Evolution has been set up in your new installation, those can simply be pasted into the new installation's .evolution directory to overwrite the files of the same name. That will carry forward all of your old email, contacts, calendar appointments and so on. Sometimes a reboot is necessary for the changes to appear.

Open your firefox web browser in your new installation. 
Have the bookmarks file of your choice copied out of your backups folder or wherever you kept it and pasted out in the open in your /home/username folder ready to be imported.
Click 'Bookmarks', then 'Manage Bookmarks', then on the 'File Menu' of the 'Bookmarks Manager' window, click 'import'. That will start the 'import wizard'. Click 'next', and navigate to your '/home/username' folder. Find your bookmarks file to be imported and click 'Open'.

Paste in any other hidden files for programs you use that you may be important to you.

It's pretty simple stuff really.

Of course, having a separate /home avoids a few minutes of copying and pasting work to restore from the backup, but we still need to have an up to date backup of especially our most important files and settings .

My concern is for new users who may believe that having a separate /home will actually 'protect their data' so they may think they don't need any backup, so they won't bother learning what to back up and why, or how to restore. Humans are lazy by nature, and I'll bet there would be a lot of people who have been using Ubuntu for some time and don't know how to back up and restore.

Of course there's also SBackup and SRestore programs too, those make backing up and restoring a breeze.

If anyone is reading this and they haven't made a backup recently, please do so now for your own sake, and don't fall into the trap if you have a separate /home, of beleiving your data will somehow be protected. There are still a lot of ways you can lose all of it in an eye-blink.

Regards, Herman :)

---

### Post by ee19921 on 2009-05-02
Sorry to barge in here. Can you also help me out [here]("http://ubuntuforums.org/showthread.php?t=1146669")?

---

