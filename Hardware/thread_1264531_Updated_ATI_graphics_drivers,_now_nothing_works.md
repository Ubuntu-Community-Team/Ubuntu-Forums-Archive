---
title: "Updated ATI graphics drivers, now nothing works"
date: 2009-09-12
forum: Hardware
---

### Post by impervius on 2009-09-12
Ok, so im running Jaunty, and one of my programs complained that i wasn't using the latest graphics drivers. I tried to install the newest drivers on the ATI website, but they wouldn't work.

I googled the error message and found a site saying to execute the command 

"aticonfig --initial -f"

i did this and restarted. Now i get the Ubuntu loading screen, followed by a mess of random pixels gradually growing brighter. I can't actually get into the main OS so i cant change any options.

What can i do??

---

### Post by MelDJ on 2009-09-12
try going into recovery mode and typing the command there

---

### Post by impervius on 2009-09-12
im getting "aticonfig: No supported adaptors detected"

before it told me to to an apt-get when i put this

what should i put to get rid of what i installed

---

### Post by MelDJ on 2009-09-12
hm..try uninstalling all the drivers and reinstalling it again from the ati website

---

### Post by impervius on 2009-09-12
how can i uninstall the ati drivers by command line

---

### Post by impervius on 2009-09-12
anyone? how can i uninstall the drivers

---

### Post by MelDJ on 2009-09-12
these might help: [http://ubuntuforums.org/showthread.php?t=517225](http://ubuntuforums.org/showthread.php?t=517225)
                            [http://ubuntuforums.org/showthread.php?t=630418](http://ubuntuforums.org/showthread.php?t=630418)

---

### Post by impervius on 2009-09-12
i saw in another thread

To uninstall just go into terminal and type in
cd /usr/shar/fglrx/
sudo sh ./fglrx-uninstall.sh
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=1133581") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=1133581")
but this gives a file or directory doesn't exist for me

---

### Post by MelDJ on 2009-09-12
you should cd to the folder where the drivers are in your computer

---

### Post by NexusZA on 2009-09-12
> **impervius said:**
> i saw in another thread

To uninstall just go into terminal and type in
cd /usr/shar/fglrx/
sudo sh ./fglrx-uninstall.sh
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=1133581") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=1133581")
but this gives a file or directory doesn't exist for me

The location is actually /usr/src/fglrx-[version] so in terminal type:

```
cd /usr/src/fglrx
```

then press TAB a couple times to let it auto complete the directory name, then continue with uninstall:

```
sudo sh ./fglrx-uninstall.sh
```

---

