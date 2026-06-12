---
title: "Application closes for no reasons"
date: 2008-07-13
forum: General Help
---

### Post by phil81uk on 2008-07-13
Morning,

I installed the aMule P2P application on Ubuntu (similar to eDonkey/eMule), and left my laptop running overnight while aMule downloaded some files. However, each time I went to check on the laptop the application was not there and I had to reopen it.

Is there any reason why Ubuntu might close down this application?

Regards

---

### Post by pooyaplus on 2008-07-13
Hi,
Run the app in the Terminal and see what's happening.
I can remember a bug with the amule sometime ago, that the app would crash if you close the tabs e.g. search tabs. See if the issue is solved in the latest version and get the latest version from the project website.

goodluck.

---

### Post by phil81uk on 2008-07-13
> **pooyaplus said:**
> Run the app in the Terminal and see what's happening.

What does this mean please?

---

### Post by jefe on 2008-07-13
Just run gnome-terminal or konsole (I KDE) from menu, then in terminal type the program you would like to run, instead starting it directly from menu. In this case just type amule. Then copy all infos and paste it so we can see them.

---

### Post by pooyaplus on 2008-07-13
Go to Applications>Accessories>Terminal
Then type amule.
And post the output of the terminal here when the app crashes.

---

### Post by actarus000 on 2008-08-05
Hi

I have also experienced Amule closing unexpectedly after a couple of hours.

I am running it on Ubuntu HH.

I have read that some crashes were caused by incoming messages, so I filtered those, to no avail.
I have ticked the "confirm before closing" box, to no avail.

What can one do ?

Here's the transcript of running Amule from the terminal

nicholas@nicholas-desktop:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
Loading temp files from /home/nicholas/.aMule/Temp.
Loading PartFile 93 of 93
All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Adding file /home/nicholas/.aMule/Temp/075.part.met to shares
Adding file /home/nicholas/.aMule/Temp/072.part.met to shares
Adding file /home/nicholas/.aMule/Temp/070.part.met to shares
Adding file /home/nicholas/.aMule/Temp/069.part.met to shares
Adding file /home/nicholas/.aMule/Temp/068.part.met to shares
Adding file /home/nicholas/.aMule/Temp/066.part.met to shares
Adding file /home/nicholas/.aMule/Temp/064.part.met to shares
Adding file /home/nicholas/.aMule/Temp/063.part.met to shares
Adding file /home/nicholas/.aMule/Temp/062.part.met to shares
Adding file /home/nicholas/.aMule/Temp/061.part.met to shares
Adding file /home/nicholas/.aMule/Temp/060.part.met to shares
Adding file /home/nicholas/.aMule/Temp/058.part.met to shares
Adding file /home/nicholas/.aMule/Temp/057.part.met to shares
Adding file /home/nicholas/.aMule/Temp/055.part.met to shares
Adding file /home/nicholas/.aMule/Temp/054.part.met to shares
Adding file /home/nicholas/.aMule/Temp/053.part.met to shares
Adding file /home/nicholas/.aMule/Temp/099.part.met to shares
Adding file /home/nicholas/.aMule/Temp/095.part.met to shares
Adding file /home/nicholas/.aMule/Temp/091.part.met to shares
Adding file /home/nicholas/.aMule/Temp/090.part.met to shares
Adding file /home/nicholas/.aMule/Temp/088.part.met to shares
Adding file /home/nicholas/.aMule/Temp/086.part.met to shares
Adding file /home/nicholas/.aMule/Temp/085.part.met to shares
Adding file /home/nicholas/.aMule/Temp/083.part.met to shares
Adding file /home/nicholas/.aMule/Temp/081.part.met to shares
Adding file /home/nicholas/.aMule/Temp/078.part.met to shares
Adding file /home/nicholas/.aMule/Temp/076.part.met to shares
Adding file /home/nicholas/.aMule/Temp/028.part.met to shares
Adding file /home/nicholas/.aMule/Temp/027.part.met to shares
Adding file /home/nicholas/.aMule/Temp/025.part.met to shares
Adding file /home/nicholas/.aMule/Temp/017.part.met to shares
Adding file /home/nicholas/.aMule/Temp/014.part.met to shares
Adding file /home/nicholas/.aMule/Temp/013.part.met to shares
Adding file /home/nicholas/.aMule/Temp/012.part.met to shares
Adding file /home/nicholas/.aMule/Temp/011.part.met to shares
Adding file /home/nicholas/.aMule/Temp/010.part.met to shares
Adding file /home/nicholas/.aMule/Temp/009.part.met to shares
Adding file /home/nicholas/.aMule/Temp/008.part.met to shares
Adding file /home/nicholas/.aMule/Temp/005.part.met to shares
Adding file /home/nicholas/.aMule/Temp/052.part.met to shares
Adding file /home/nicholas/.aMule/Temp/051.part.met to shares
Adding file /home/nicholas/.aMule/Temp/049.part.met to shares
Adding file /home/nicholas/.aMule/Temp/048.part.met to shares
Adding file /home/nicholas/.aMule/Temp/047.part.met to shares
Adding file /home/nicholas/.aMule/Temp/041.part.met to shares
Adding file /home/nicholas/.aMule/Temp/039.part.met to shares
Adding file /home/nicholas/.aMule/Temp/038.part.met to shares
Adding file /home/nicholas/.aMule/Temp/036.part.met to shares
Adding file /home/nicholas/.aMule/Temp/031.part.met to shares
Adding file /home/nicholas/.aMule/Temp/030.part.met to shares
No shareable files found in directory: /home/nicholas/Amule downloads
No shareable files found in directory: /home/nicholas/Musique
No shareable files found in directory: /home/nicholas/Musique/Badly Drawn Boy
Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

---

### Post by Logan 1229 on 2009-06-25
This is an old but obviously still valid thread. I have just experienced this same problem.  Have been running 9.04 since it came out.  Previously no amule problems.  When ran amule in terminal, same basic message as posted by actarus000, ending as:

Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

Ideas?

---

### Post by pooyaplus on 2009-06-27
Hi,

are you trying to connect to the service behind a translucent proxy or some form of firewall protection.

Cheers.

P.

P.S. try finding another URL (for the servers) from the amule forums.

---

### Post by Logan 1229 on 2009-07-01
My server list was fine.  Ended up finding solution here (thanks to Festor):

[http://www.amule.org/amule/index.php?PHPSESSID=c9a20141a9b8031bf440b957a146d373&topic=16647.0](http://www.amule.org/amule/index.php?PHPSESSID=c9a20141a9b8031bf440b957a146d373&topic=16647.0)

I had just started getting new links from [www.sharethefiles.com](www.sharethefiles.com), as [www.shareheaven.net](www.shareheaven.net) appears to have been "shut down"--anyone heard why? (I haven't come across a reason while surfing...)

Installed amule-gnome-support package via synaptic package manager.  Seems to have solved the problem.  (Thanks to all for help)

---

