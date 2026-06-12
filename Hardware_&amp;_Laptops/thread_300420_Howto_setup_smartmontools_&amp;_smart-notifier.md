---
title: "Howto setup smartmontools &amp; smart-notifier"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by SonWon on 2006-11-15
I am trying to setup smartmontools and smart-notifier.  I installed them with synaptic.

I added -M test to the /etc/smartd.conf file but when I restart smartmontools to test there is no message?

Can someone help?

Thank you,
SonWon

---

### Post by SonWon on 2006-11-15
Never mind I just figured it out.

You can only have one DEVICESCAN line in the /etc/smartd.conf file and I had two by mistake.

SonWon

---

### Post by frafu on 2007-02-25
Hello, 

I installed smartmontools and the smart-notifier by using the Synaptic Package Manager. 

Further, I read that it was possible to test whether it works by adding "-M test" to the DEVICESCAN line. However I don't see any notification when the computer starts up. (I don't think that it is because the computer is headless and because I am using vnc.) 

/etc/init.d/smartmontools stop followed by 
/etc/init.d/smartmontools start also does not produce any notification.

However, if I use smartmontools interactively in the terminal, it gives me the state of the harddisks. 

Could anybody give me any advice? 

Thanks in advance. 

Francesco

---

### Post by SonWon on 2007-02-25
Post your /etc/smartd.conf file with the -M option and I will see if it looks ok?  Also post it without and I'll compare to my file.

---

### Post by frafu on 2007-02-25
Hello, 

In fact, it was the original smartd.conf file with only one change: 
I  appended "-M test" at the end of the line; but I did not get any notification. 

Then, I tested by removing the original "-M exec..." part of the line to replace it with "-M test", but this did not work either. I have now restored the smartd.conf file to its original state; so there is probably no need to post them. 

Here is what I altered: 
1st try: 
```

...
DEVICESCAN -m root -M exec /usr/share/smartmontools/smartd-runner -M test
...

```

2nd try: 
```

...
DEVICESCAN -m root -M test
...

```

Something that I don't understand: I thought the -m switch was for sending an email, but the line contains "-m root". The word "root" is not an email address for what I know. Consequently, what does that mean? 




I would like to monitor 2 ide and 2 sata disks with smart: 
/dev/hda
/dev/hdb
/dev/sda
/dev/sdb

I know that for sata drives, I have to explicitely give "-d ata", to tell it to address the disks like ata drives and not scsi drives, but I only altered the DEVICESCAN; thus I suppose that it does not come into account. 


Maybe another question: where is the command that tells to smartmontools to use smart-notifier? Or I could ask: How does smartmontools know to use smart-notifier? 


Thanks in advance for any help. 

Francesco

---

### Post by SonWon on 2007-02-25
I think when I tested I used:

```
DEVICESCAN -m root -M test /usr/share/smartmontools/smartd-runner
```

It has been awhile so I am not sure.

Or:

```
DEVICESCAN -m root -M test exec /usr/share/smartmontools/smartd-runner
```

My current line is:

```
DEVICESCAN -m root -M exec /usr/share/smartmontools/smartd-runner
```

You could also check at [Smartmontools-support]("https://lists.sourceforge.net/lists/listinfo/smartmontools-support")

---

### Post by frafu on 2007-02-26
Hello,

I also don't get any error message with your variations. 

I am wondering if smartmontools is running!? When I do
ps -auxc | grep smart in the terminal, I only get 2 instances of
smart-notifier. 

I have to dig further... 

Nevertheless, thanks for your help. 

Francesco

---

### Post by SonWon on 2007-02-26
I have smartd and smart-notifier running on my system.

---

### Post by frafu on 2007-02-26
So, the problem probably is that smartd does not run. 

Any idea how I can start it? 

sudo /etc/init.d/smartmontools start 
does not start smartd

---

### Post by frafu on 2007-02-26
I had to edit /etc/default/smartmontools and uncomment start_smartd=yes

Now smartd is also running. 

Remains the problem with the notifications...

---

### Post by SonWon on 2007-02-26
I dug around and found these notes I created from when I installed.

```
Installed smartmontools and smart-notifier.
edit /etc/default/smartmontools un-commenting the start_smartd=yes line
add /usr/bin/smart-notifier to your gnome session
Then, to test it:
* edit /etc/smartd.conf and add "-M test" to the configuration line, this will cause smartd to send a test message on each restart. The line should look something like:
DEVICESCAN -m root -M test -M exec /usr/share/smartmontools/smartd-runner
* running `sudo /etc/init.d/smartmontools restart` should cause a fake warning message window to pop up.
```

Sorry, I didn't remember them sooner.

---

### Post by frafu on 2007-02-26
Many thanks for your help and your notes. I succeeded to get the fake notification and I think that now it is running as it should. 

Have a nice day. 

Francesco

---

### Post by SonWon on 2007-02-27
Your welcome!

I am glad I was able to contribute to the community.  I've been using Ubuntu since August 2005 and still learning.

---

### Post by frafu on 2007-02-27
For those who might be interested: I commented the DEVICESCAN line in smartd.conf and added the following lines to it to monitor my 4 disks: 

```
 
/dev/hda -n standby,q -a -m root -M exec /usr/share/smartmontools/smartd-runner
/dev/hdb -n standby,q -a -m root -M exec /usr/share/smartmontools/smartd-runner
/dev/sda -d ata -n standby,q -a -m root -M exec /usr/share/smartmontools/smartd-runner
/dev/sdb -d ata -n standby,q -a -m root -M exec /usr/share/smartmontools/smartd-runner

``` 

(Please, don't simply copy the above lines to your system, as I am not sure whether they are correct.) 

-d ata: to force smartmontools to address sda and sdb as ide devices, and not as scsi devices; in fact, sda and sdb are sata harddisk

-n standby,q: to suppress the test when the harddisk is in standby or sleep; otherwise the harddisk has to spin up to do the test

-a: perform the usual tests; 

-m root -M exec ...: this makes smartmontools ?send an email? and run the executable defined after the keyword exec; in my particular case where I also installed the "smart-notifier", it makes a notification window appear. 

However, I don't fully understand the lines: 
- usually there is an email address instead of the word root after -m; what does the keyword root mean in that context? 
- does I get a notification window because of the executable smartd-runner? 
- how often is a poll/test done? I suppose it uses the disks default, in other words every 4 hours!? 

Any comment helping me to understand somewhat more what is going on is welcome. 

Have a nice day. 

Francesco

---

### Post by kilou on 2007-06-02
> **SonWon said:**
> I dug around and found these notes I created from when I installed.

```
Installed smartmontools and smart-notifier.
edit /etc/default/smartmontools un-commenting the start_smartd=yes line
add /usr/bin/smart-notifier to your gnome session
Then, to test it:
* edit /etc/smartd.conf and add "-M test" to the configuration line, this will cause smartd to send a test message on each restart. The line should look something like:
DEVICESCAN -m root -M test -M exec /usr/share/smartmontools/smartd-runner
* running `sudo /etc/init.d/smartmontools restart` should cause a fake warning message window to pop up.
```

Sorry, I didn't remember them sooner.

Hi,

I did that but when I sudo /etc/init.d/smartmontools restart I get:
 * Restarting S.M.A.R.T. daemon smartd                                   [fail] 

But if I comment the DEVICESCAN line and add /dev/sda -d ata -n standby,q -a -m root -M exec /usr/share/smartmontools/smartd-runner as suggested by frafu then smartd can be started correctly (I use Feisty and my IDE HDD is /dev/sda instead of /dev/hda). However even if I add -M test I still don't get any notification after restarting smartd. Any idea why??? ...and how to use smart-notifier??

SOLVED:...this was simply because I did not already restart the system so smart-notifier wasn't launch. When it is started I get the notification :)

---

### Post by frogotronic on 2008-04-13
Okay, I've followed the instructions, but I dont see any graphical output at all.

What am I doing wrong?

---

### Post by AndrewTheArt on 2008-07-11
> **cement_head said:**
> Okay, I've followed the instructions, but I dont see any graphical output at all.

What am I doing wrong?

I have the same problem. Anyone have any ideas?

---

