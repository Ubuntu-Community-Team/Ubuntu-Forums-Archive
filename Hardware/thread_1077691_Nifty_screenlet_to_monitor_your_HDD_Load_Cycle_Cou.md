---
title: "Nifty screenlet to monitor your HDD Load_Cycle_Count in Ubuntu"
date: 2009-02-22
forum: Hardware
---

### Post by seemanta on 2009-02-22
Hi,

I am sure many of you are planning to or already applied the 'ugly' fix
for the Load_Cycle_Count issue. In any case, you might have wondered if 
there was some nifty way to keep an eye on the load cycle count. 

This may be necessary for 2 reasons:

1. You want to give a trial run of what hdparm values work best for you
before you make those hdparm values permanent within the /etc/resume 
folders as mentioned by ubuntudaemon in his fix.

2. You have applied the fix, but still you are paranoid and want to 
monitor your HDD Load_Cycle_Count. Personally, I fall in this category.

Whatever your reasons are, it would definitely be nice to have a always
on screenlet on your desktop to help you keep an eye over your Load_Cycle_Count.

So follow these steps and start monitoring:

Step 1: Get the screenlets package. Also install cron daemon if you do 
not have it. Chances are cron would be already installed as part of the 
base system. You would also need the smartmontools to query your HDD 
parameters.

```
bash$ sudo apt-get install screenlets cron smartmontools
```

Step 2: Download the bash shell script called 'HDmon.sh' attached with this post and copy it to /etc/init.d

```
bash$ sudo cp /wherever/you/downloaded/HDmon.sh /etc/init.d
```

Step 3: Edit crontab file for root so that the HDmon.sh script gets 
called every minute.

```
bash$ sudo crontab -e
```

This will open up an editor. The file would probably look like this, in 
case you have never updated crontab for root user before:

```
 # m h  dom mon dow   command
```

Update the file so now it looks like this:

```

# m h  dom mon dow   command
*  *  *  * *  /etc/init.d/HDmon.sh

```

In case you are wondering what the 5 stars stand for, it means that we 
are asking cron scheduler to run the shell script at /etc/init.d/HDmon.sh 
every minute, 24 hours a day, 365 days a year. For more details, type 
'man cron' at the shell prompt.


Step 4: Open up screenlets manager from 
Applications-->Accessories-->Screenlets. Here is a screenshot of where to
find it, assuming your screenlets installation was proper at Step 1.

[IMG]http://seemanta.files.wordpress.com/2009/02/screenshot_01.png[/IMG]


Now, within the screenlets manager, select the 'Output' screenlet and 
then click on the 'Start/Stop' checkbox at the bottom left corner.

This will bringup the 'Output' screenlet. However, it would show the 
output of 'dmesg' command by default, which we don't want.

Here is a screenshot with instructions on how to do that, with the steps 
numbered for convenience:

[IMG]http://seemanta.files.wordpress.com/2009/02/screenshot_04_ret.png[/IMG]

We now need to change the screenlet properties so that it shows our 
Load_Cycle_Count data rather than 'dmesg'.

This can be done by right clicking on the screenlet and then selecting 
'properties'. This will open up a configuration window. There you need to 
mention the command to read a file from /tmp in order to display the 
Load_Cycle_Count within the screenlet. I will explain shortly what this 
file is.

Here is another screenshot to help you do that:

[IMG]http://seemanta.files.wordpress.com/2009/02/screenshot_06.png[/IMG]


There you go! You can now keep a tab on the Load_Cycle_Count of your hard 
disk in real time! That's it! You are good to go. Enjoy!


Here is a screenshot how it looks after everything has been done:

[IMG]http://seemanta.files.wordpress.com/2009/02/screenshot_07.png[/IMG]

Read on if you are interested on how everything was done, behind the 
scenes.

Remember the HDmon.sh shell script that you copied at the beginning? That 
basically just queries the HDD parameters using 'smartmontools'. But  
that script dumps that data into two files within /tmp:  HDmonStat.out 
and HDmon.out.

Don't worry, these files are plain text files and would get deleted the 
next time you reboot your machine. If you do a 'cat' of the file 
'HDmonStat.out' you would find that this file contains the same data that 
you can see in the output screenlet. Yeah, you guessed it! The screenlet 
just 'cat's the 'HDmonStat.out' file periodically. And this file gets 
regularly updated via cron with the latest Load_Cycle_Count statistic.


There is another file, called 'HDmon.out', if you have noticed. Well, 
this is a detailed statistics file which contains the minute by minute 
information about Load_Cycle_Count. This file is helpful if you are 
trying out the ugly fix for the first time and want to check how fast or
 slow your Load_Cycle_Count and HDD temperature rises for a particular 
value of hdparm.

For the record, the screenlet shows the following information:

a) Current Date and time
b) Current HDD APM settings, or the current parameter to your hdparm -B command.
c) Total Load_Cycle_Count
d) The hard disk temperature in degree Celsius. You should be monitoring this in case you are trying out the 'ugly' fix for the first time.
e) Now this figure is very important. This shows the average Load_Cycle_Count per hour. This should be your guiding metric when deciding values for your hdparm for your 'ugly' fix.

And yes, I arrived at hdparm setting of 254 on AC and 250 on battery using this little screenlet. But this was for my HDD and the actual numbers would vary for your hard disk.


I hope this post was useful to you. Do write back your comments!

regards,
Seemanta

P.S. Some hard disks give the Load_Cycle_Count value in the raw format 
i.e. something like 4550305. This does not mean the load cycle is 
actually that much, but means that the data has to be processed to arrive 
at the actual value. My HDD fortunately gives the actual load cycle count 
and so my HDmon.sh script does not do any processing. So if you use my 
script for such a HDD which gives a raw output with smartmontools, then 
this may not be that helpful.

I would be grateful if you modify and redistribute the HDmon.sh script to suit your purpose. You may also download this script from [http://seemanta.net/code/UbuntuScreenlet/]("http://seemanta.net/code/UbuntuScreenlet/") in case you do not have an account in Ubuntuforums.

---

### Post by eimor on 2009-03-30
Hi, great how to:), but does not seem to work for me:(, you lost me in the crontab part, and i guess if that is not done correctly then loading the line "cat /tmp/HDmonStat.out" does nothing, cause the screenlet show no data, hope you can help me. Dont know if i have the crontab service activated on start up ? where do i get the info about that? by the way, when i try the "crontab -l" comand, i get "no crontab for juan" (juan is my user). Hope you can help mi cause i did the hdparm thing and currently don't know my sda temp unless i use terminal (kind of annoying)

---

### Post by seemanta on 2009-03-31
eimor,
Try crontab -e. Does that work for you? -e means you want to edit. -l just lists the cron jobs. Since you don't have any crontab -l says no crontab for user. But I guess you do have cron installed else crontab -l itself would not have worked.

Just in case crontab -e does not work then cron is probably not installed. Go to synaptics, search for cron and then install it. Using commandline it might be:

apt-get install cron

Not sure if it was cron or crond so better you use synaptics to search and then install.

---

### Post by eimor on 2009-04-01
Took a look at synaptics and cron is installed, the cron -e works, i did exactly what you posted and then alt+x or ctrl+x to save the changes, if i went and did cron -e it showed the modified version i did. But the thing is i think the hd process is not being called, and so i cannot find the "hd**.out" file in the tmp folder. So when i type the cat command in the screenlet configuration nothing happens and the screenlet doesnt present any data. What am i doing wrong?

p.s.:thanks for the reply

---

### Post by seemanta on 2009-04-01
eimor,
Edit your /etc/init.d/HDmon.sh script and just after #!/bin/bash lipne add this line:

> touch /tmp/cron_works

So the HDmon.sh script will look like this:

> #!/bin/bash

touch /tmp/cron_works

# usage " sudo ./HDmon.sh <time_to_refresh> <file_to_create>
# where time_to_refresh is an integer which tells after how many seconds
# the SMART readings should be refreshed.
.
.
.


Now after a while check /tmp. If a file called cron_works gets created then it means that cron is calling your HDmon.sh script properly.

Also check if smartctl works from the command line by trying:

> sudo smartctl -a /dev/sda

Let me know what happens after this.

~seemanta

---

### Post by eimor on 2009-04-02
sudo smartctl -a /dev/sda is working great, but the corn_works file did not appear, what can i do?

---

### Post by eimor on 2009-04-03
ha ha, not CORN, cron_works, hahaha, my brain is toasted

---

### Post by eimor on 2009-04-03
GOT IR WORKING!!!!, i think, hope next boot up it is still there. Any problems i`ll report back here, turns out the HDmon.sh file was no executable, got into Nautilus through gksudo nautilus, right clicked on the HDmon.sh file, and clicked on the checkbox to allow to run as a program and presto.

---

### Post by eimor on 2009-04-03
Here you have a screen cap

[IMG]http://img523.imageshack.us/img523/9458/pantallazo1m[/IMG]

---

### Post by eimor on 2009-04-03
[IMG]http://img523.imageshack.us/img523/9458/pantallazo1m.png[/IMG]

here it is

---

### Post by Rossi9x87 on 2009-04-03
im not sure if it was mentioned so far, but once you move the HDmon.sh file into the /etc/init.d directory, you need to set it as an executable text file.  Otherwise, cron will not be able to poll it and assess your load cycles. 
The way to identify this is if you get the output of:

"cat: /tmp/HDmonStat.out no such file or directory"

in your output box.


Thanks guys this little screenlet is pretty sweet!
-jkb

---

### Post by eimor on 2009-04-04
The good news is it works, the bad news is it does not load on startup, tried everything (using screenlets-manager and setting "output" screenlet to load on logon, using a script referencing to the "output" python file, etc.) but the only way to make it appear is right clicking on the screenlets-manager icon on the tray and using "restart all screenlets". Do you know any workaround for this?

---

### Post by seemanta on 2009-04-08
Hey sorry about not being able to reply to you earlier! I was going to suggest you to try `ps- eaf| grep cron` to see if cron daemon is running, but looks like you have already solved the problem!

I am glad that you were able to make it work! Cool! 

regards,
Seemanta

P.S. Your screenshot looks real nice too!

P.P.S. Saw your latest updated message just now, where you mentioned that it does not work at startup. Well, for me it does. I just checked the 'Auto start on login' field when enabling the screenlet. Here, take a look at this screenshot attached where I have highlighted that part with a red rectangle. Let me know if it does not work even after this.

---

