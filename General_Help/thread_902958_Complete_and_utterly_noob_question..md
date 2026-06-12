---
title: "Complete and utterly noob question."
date: 2008-08-27
forum: General Help
---

### Post by rwenzel on 2008-08-27
Hello,

Thank you for reading this. I just built a new pc and I wish to create a server. 

The goals of the server in order of its timeline, are as follows:

(Please note that when I say drive, I mean a physical drive, not space/partition)

To create a storage facility for my gf who spends half her time in China on 2 drives, (im in ny).

To once per day back up that data onto two separate hard drives (each mimicing the other).

One additional drive for putting media content that will be shared with a windows environment.

To install FirebirdSQL database.

To install a C++ development package (havent picked one out yet, but anjuta looks nice)

To write code that will take a feed from electronic data provider for security prices, store that data in the firebirdsql database.

Install Scilab and use that for modeling purposes on the above data. All of the data will also be backed up daily. 

I foresee this pc having 8 drives initially. If everything pans out, the data collection/storage/modeling will be moved to a separate pc.

Okay, I know a bit about programming. But calling me a programmer would be a far stretch. But I am not worried about the programming aspect of it. My problem is that I know nothing about UNIX/LINUX environments. Well ages ago, I used a Sparc workstation, but for only a few mathematical models with some scripted commands I typed in, and I barely remember some command line items. In addition, I know very little about networking/setting up a pipeline etc.

All I am asking is for someone to recommend a book and/or a place to start learning. The book hopefully will be the hold your hand type because you get frustrated like a 2 year old having their favorite toy given to your older sister, and she enjoys that way too much. I know I won't find one that answer all of this specifically, but something that starts off with the basics and shows how to set up a storage that a windows pc can assign a drive letter too, and move files back and forth easily (this part if for my gf).

I bought the Official Ubuntu book, but that was a mistake. I am sure its a good book, but its much more oriented to the windows like environment of the non-server release.

Details of the system, if important. AMD Toliman 8450, 2g of Mushkin ram (if this starts to take off  beyond the backup server and media station, will go to 6gb), seagate ES hard drives, amd 790gx motherboard. Will inherit my 8800gt when I feel like upgrading my other pc. Corsair tx750.

The goal of this is more of a proof of concept for me. Not to build a live trading station, just to see what it takes to do it. If I get highly highly motivated, I will make it much more "production" level.

Any pointers/tips would be appreciated.

Thank you,
Rich

---

### Post by cariboo on 2008-08-27
Have a look here:

[http://tldp.org/](http://tldp.org/)

There is a lot of documentation here from howto's to in depth manuals.

Jim

---

### Post by rcrcomputing on 2008-08-28
I don't know of a book for you. Just a few hints though.
To share data between the two has always meant a fat32 partition they can both read-write to.  However, be aware of the file size limit whitch I'm thinking is 4gig though it may be 2gig. Is writing to ntfs a stable thing to do? I don't know. It used to not be..  

To sync the first two drives, the program to use would be rsync. Run nightly with a cron job. [http://programs.rcrnet.net](http://programs.rcrnet.net) might be a place to start with rsync. It's one of my "works in progress".

You will want to install ssh on the server and then ssh into it to work on it from your pc after initial setup. I suggest using a key file with ssh. The link above rsync_backup_local will create and upload the key for you. 
Also remember SSH is vulnerable by it's very nature of letting someone bang passwords at it till they get one right. Use a firewall to limit incoming ssh to certain ip's and after you upload your key file, turn off password log-in.

Remember, your memory is limited to 4gig if you don't have a 64bit OS.

You do NOT need a GUI on the server. You'll not be sitting in front of it anyway. However, webmin is a blessing.

---

### Post by rwenzel on 2008-08-28
thank you very much for the tldp link, its very useful. I will learn a lot.

rcrcomputing, thank you for your suggestions and I will look at that link. Ubuntu server is 64-bit.

thank you.

rich

---

