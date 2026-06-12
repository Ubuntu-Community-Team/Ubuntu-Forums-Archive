---
title: "Outlook pst file to evolution"
date: 2008-08-26
forum: General Help
---

### Post by sekhorr on 2008-08-26
Hi All,
I have read many posts concerning the conversion of Outlook pst files to maildir, mbox and other formats inorder to be able to be imported into evolution. Almost all of them require Windows to convert the pst files to some format and then copied over to Ubuntu for import into evolution.

Now, my question is, I have the pst file copied to Ubuntu 8.04 and now i want to use Ubuntu (and follow some procedure) to convert the pst file to the required usable format for evolution. Can I do that without the help needed from Windows at all? Please advise.

What is the best option to convert pst files to some format in evolution?
Thank you all in advance.

---

### Post by SirDevan on 2008-09-04
I also have this issue. I copied my pst files out of Outlook and stored them on the network, then formatted and installed Ubuntu 8.04. Now I can't seem to find any way of importing my mail/contacts short of virtualbox/vmware windows install outlook etc.

After a week of searching 99% of what I find was posted 4 years ago. Is there still nothing that makes this process non painful??

Devan

---

### Post by Ms_Angel_D on 2008-09-04
I found this thread on importing outlook to evolution

[http://ubuntuforums.org/showthread.php?t=53138](http://ubuntuforums.org/showthread.php?t=53138)

---

### Post by SirDevan on 2009-03-11
Yes, that still requires windows. As you see I am back after 6 months and still no feasible way to import a pst file without requiring windows. I don't understand why this is so difficult. If there is a program in windows that can do it why can't we do it in Ubuntu? I moved to Ubuntu with NO windows because I hate windows, and now, for the first time I am finding that windows can do something Ubuntu can't.

No one has any clue on this? I would pay $50 for a program that would do this successfully and I can't even find that.

Devan

---

### Post by rbmorse on 2009-03-11
Microsoft owns the .pst file format used in Lookout! and to date hasn't licensed any third-party use. In effect, Microsoft owns your data. Outlook is probably well up in the list of top ten reasons people decide to move off Microsoft applications and operating systems.  It's one of the most egregious examples of vendor lock-in I've eve seen.

I don't have a direct answer, but since you've indicated you would spend some money for the cause I can propose a science project, if you're interested. Little Machines [http://www.littlemachines.com]("http://www.littlemachines.com/") sells a Windows application named O2M for $10 that will convert your .pst file into files that can be used with Apple's OS X operating system.  What Little Machines doesn't mention is that output of O2M are open format mbox, ical and vcf files that are usable by most Linux mail, calendar and addressbook applications. I've used O2M (from Widows) and the resulting files work fine with Evolution, Thunderbird/Lightning and Kontact (KDE 3.5). 

The science project is to see if O2M runs under either WINE (free, available in repository) or Crossover Office, not-free, but available on a free-trial basis from [http://www.codeweavers.com]("http://www.codeweavers.com/").  

In fact, give me a minute and I'll try it here.

---

### Post by rbmorse on 2009-03-11
Me again with results from the experiment to run O2M under Crossover Office 7.  Unfortunately, it fails. 

O2M installed cleanly into Crossover Office 7 running on Ubuntu 8.10. The program, however, requires Microsoft Outlook to be installed and running at the time it converts the .pst file to open formats.  My version of Outlook (2003) will install and run under Crossover Office, but I don't Outlook installed on this machine and I don't have time to find an available copy and install it so I can do the O2M extraction part of the experiment right now.  

Sorry for any confusion.

---

### Post by Cheesemill on 2009-03-13
How about using [readpst]("http://alioth.debian.org/projects/libpst/").
Man page is [here]("http://alioth.debian.org/docman/view.php/30390/47/readpst.1.html").

Cheesemill

---

### Post by alecwk on 2009-12-23
Sometimes we have to go round and round only to find that the solution is right in front of us. And this just happened to me. 

Importing Outlook .pst file into Evolution is as simple as go to Evolution and Import it!!!

I am using Evolution 2.28.1 bundled with Ubuntu Karmic. Start your Evolution, go to File>Import. A window will pop up, choose "import a single file", choose the .pst file you want to import and tick what you want to import and press forward. As simple as that. 

You may have to try a few times importing the .pst file before you get all your files imported. I had a somewhat corrupted .pst file, I can't even import to another Outlook. The Evolution did it well enough. Its an Evolution!!

---

### Post by Hey Gary on 2010-01-24
Alecwk is correct, there is now (in Evolution 2.81.1) an option under Import a Single File where you can select an outlook PST file.

A few points you should be aware of.
1- If you have a folder (maybe Inbox) that has messages in it, and it has nested folders under it, you should move (not copy) all the Inbox messages to a new folder under the inbox.  The idea is that any folder which has subfolders should not have messages too.

The reason is that the import places ALL the messages in the next folder down.  So if you have inbox and nested under it is a folder named work and you have personal stuff in inbox and work related in work, after the import all your email is in the work folder.  Solution, create a subfolder of inbox, call it "inbox saved" and move all the inbox email to inbox saved.

2- Importing will import all messages, importing a second time will duplicate all messages.

3- Notes from outlook do not copy over.  Notes can be copied as a .CSV file, but evolution uses Memos which are more like ical appointments.  Importing them will make them appear as contacts... not quite what you want.  IT WOULD BE GREAT if during the import of a CSV into Evolution I could select the destination folder and map the CSV columns to fields of the type for that folder, but that feature does not exist (yet?).

4- I found calendar entries not copying correctly.  Regular appointments are fine, but recurring appointments (birthdays and anniversaries) copy as a start and end date, 2 days long for the event.  I suggest you export from Outlook to a CSV file.  You can import a CSV but you can also examine it and make changes as needed.  The CSV format does not include recurrences, so you have to fix those manually either way.  You should change them to single occurrences, then in Evolution edit them to make them recur again.

5- Contacts - All contact folders in outlook (if you use more than one, are merged into the single contacts folder when importing from the PST file.  I found a solution to export each contact folder as a separate CSV file.  Then you create an Address Book in Evolution and import the CSV file to the matching Address Book.  IT IS IMPORTANT that you tell the importer that the csv is an Outlook CSV as the default of Evolution will cause you problems.

6- When importing the mail and folders from a PST file, any empty folders (a folder with a subfolder is not considered empty) are not created.

I only wish there was an "Export" function in Evolution, but hey, I have files right?  :)

I hope this helps.

---

### Post by adromidon on 2010-06-25
Will this Evolution import method also import email accounts as well or do we still need to setup email accounts manaually?

---

### Post by kevinanchi on 2010-06-26
> **Ms_Angel_D said:**
> I found this thread on importing outlook to evolution

[http://ubuntuforums.org/showthread.php?t=53138](http://ubuntuforums.org/showthread.php?t=53138)


You Are Cricket right???

---

### Post by kevinanchi on 2010-06-27
> **kevinanchi said:**
> You Are Cricket right???

thaks for the help :)

---

### Post by mirkob on 2010-08-03
I have been trying to move from Windows to Linux for a while now.
At first, I tried Fedora but could never get it to connect to the printer on my wife's computer running XP. With Ubuntu it took 2 minutes.
Another obstacle will be remotely accessing my Windows VM development machine on my company network through VPN.
And last but not least is moving from Outlook.
Evolution seems nice with an integrated calendar but can I have access to all my emails ???

I have a large Outlook.pst (2GB+)
I have 26 folders, (A, B, C ...) and under them sub-folder mainly named after my account and customer names.
I probably have more than 200 folders with emails in them.
The import function in Evolution seems to accept .PST file but that's just for show. When you point to it, it does not open the file.

So I have used readpst with the -r option and it created as many MBOX file as there are folders.

Am I expected to import them one by one using the Evolution import function, re-creating the folders-subfolders structure along the way? 

Any help will be appreciated.
Thanks

---

### Post by mirkob on 2010-08-04
Turns out connecting to the Windows remote desktop was easy through VPN with rdesktop.
The Outlook thing is still laborious.
You can drag and drop an mbox file in Evolution but you still need to create the folders whic will be a lot of work.

---

### Post by meburke on 2010-08-04
I have some HUGE .pst files from defunct systems that I would like to get into evolution.

The readpst -r attempt didn't get me anything useful.

Trying to import directly from Evolution didn't work: The option for Outlook .pst files after selecting "Import single file" stayed gray'd out. I gave it time to read the file, but processes showed it wasn't doing anything.

I am running evolution 2.28.1 on Karmic, and I believe I have all the updates and upgrades installed.

I am also looking for some clues to this, because I am not running a Windows system at this time (although I am installing a virt, right now), and cannot actually manipulate the Outlook.pst files to get the messages in one folder.

BTW, what happens if Evolution gets 50,000 messages? does anyone know if there is an inbox limit?

Thanks,

Mike

---

### Post by pcrepairguy on 2011-07-09
Check out this tool that you can run from Windows with Outlook open and will convert your PST database to the format you need it. I used to migrate from Outlook to Evolution

[http://outport.sourceforge.net/](http://outport.sourceforge.net/)

---

