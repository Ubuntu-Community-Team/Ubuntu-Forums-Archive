---
title: "Tether Blackberry with 9.04"
date: 2009-05-21
forum: Hardware
---

### Post by B34N on 2009-05-21
I'm running a Dell Vostro A90 (Mini 9) with Ubuntu 9.04 and I have a Blackberry 8820 on T-Mobile (US).

The reason I'm posting this because I'm a beginner and I had a slightly difficult time finding this solution, even though it was right in front of me.  I'm hoping that I'll be able to help other beginners use their Blackberry as a modem (tether) and I also have a few unresolved questions which are included in teh below instructions.

All of the instructions and answers can be found here: [INDENT][http://www.berry4all.com/home](http://www.berry4all.com/home)[/INDENT]

The first thing I needed to do was open a terminal window and run:
[INDENT]sudo apt-get install python libusb-dev ppp python-usb[/INDENT]
That command installs the python, pppd, libusb and the python usb(pyusb) modules, which are needed to run the bbtether program.

Then I needed to run:
[INDENT]sudo apt-get install python-wxgtk2.8[/INDENT]
That command installed the graphical version of python, which I believe is only needed if you want to run the graphical version of bbtether.

Next I needed to download the bbtether package:
[http://www.colar.net/websvn/filedetails.php?repname=src&path=%2Fbbtether%2Fbbtether.tgz]("http://www.colar.net/websvn/filedetails.php?repname=src&path=%2Fbbtether%2Fbbtether.tgz")
Put the file in a folder and then extract the files from the archive.  I used the file browser and then right clicked on the file and chose the "Extract Here" option.  I'm a newbie so I'm not sure where the best place to put these files are.  I put mine in my user's home directory.  Are there any suggestions on a better place to put the files?  If I put them in my personal directory then am I keeping other users from being able to access them?

Now that everything is installed, it's time to run the program.  Since I don't know if my PPPD supports "replacedefaultroute", I followed the steps to disable my other network interfaces (eg. wifi)
Open a terminal window and run:
[INDENT]route[/INDENT]
Look at the output and it will list the interfaces.  Mine was "eth1"

Next, bring down that interface:
[INDENT]sudo ifconfig eth1 down[/INDENT]
replace eth1 with your interface.  I don't know if you need to bring down any other interfaces if you have them running.

Now you can run the bbtether program.  In the terminal window, go to the bbtether directory and run:
[INDENT]sudo ./berry4all.sh[/INDENT]
That will bring up the Berry4All graphical interface.  Then choose "Modem" and "Connect".  That will ask you for you BlackBerry password (if you have one) and which script you want to use.

Once you are done, you will need to disconnect (hang up) the modem by choosing "Modem" and "Disconnect".  This will run another script that you should give a few seconds to complete before exiting Berry4All.

The final step is very important, and it didn't work for me.  You will now need to re-enable your other connections. (eg. wifi)  To do this you will need to run:
[INDENT]sudo ifconfig eth1 up [/INDENT]
and possibly:
[INDENT]sudo /etc/init.d/networking restart[/INDENT]

The wifi didn't come back up for me, so I just restarted the machine and it was back to "normal."

I hope this post helps some of the other newbies like me!

---

### Post by dreperk on 2009-05-25
I have to say, this was very simple and helpful.  I'm not what you would consider a linux newbie, but this particular thing was the last thing that I could not do with linux.  I recently switched completely to linux and have been content, but I thought I would try tethering my blackberry one last time.  I found your instructions a lot more simple, and I used some of what I had learned in the past to suppliment them and now I'm up and running.

One thing I did was put my blackberry phone number in the configuration file as the user (in place of *"wap"*), and put my t-mobile.com login password in the place of *""* (yes, it was an empty string in quotations, right under *"wap"*).  At least it did not work for me until I did that (could be a t-mobile thing).  Thanks a lot, st8ofmi9d.

---

### Post by B34N on 2009-05-28
> **dreperk said:**
> 
One thing I did was put my blackberry phone number in the configuration file as the user (in place of *"wap"*), and put my t-mobile.com login password in the place of *""* (yes, it was an empty string in quotations, right under *"wap"*).  At least it did not work for me until I did that (could be a t-mobile thing).

I use T-mobile in the states and it works without having to include the number and t-mobile password.  Are you using T-Mobile in the states?

Another thing that I've noticed is that I don't need to bring down the interface.  I don't know if this because my PPPD supports "replacedefaultroute" or if it is because I'm not connected to any other networks when I tether the blackberry.

---

### Post by bond17_007 on 2009-08-27
Thanks for the great post.
 It worked fine when i had active wireless connection.
Followed the steps to bring my wireless down run modem etc... (after bringing my ethernet down, it automatically connected using the bb modem)

however, when i try to connect when my wirless is off it not working.

to clarify, when i am say at a park where i dont have wireless and i try to use my bb as modem, it doesnt seem to work.
 
Since, my wireless is off, when i do "route" I do not see any entry .. but after i run the bb4all program, when i run "route" i see 2 entries.. which lets be believe that i am connected  but when i try to access any website from the browser .. it is not able to connect to the internet.. i tried, firefox, chorome.. no luck
did u run into this problem before?

btw, i even ran /etc/init.d/networking restart

---

### Post by ceece on 2009-08-28
> **st8ofmi9d said:**
> I'm running a Dell Vostro A90 (Mini 9) with Ubuntu 9.04 and I have a Blackberry 8820 on T-Mobile (US).

The reason I'm posting this because I'm a beginner and I had a slightly difficult time finding this solution, even though it was right in front of me.  I'm hoping that I'll be able to help other beginners use their Blackberry as a modem (tether) and I also have a few unresolved questions which are included in teh below instructions.

All of the instructions and answers can be found here:[INDENT][http://www.berry4all.com/home](http://www.berry4all.com/home)[/INDENT]The first thing I needed to do was open a terminal window and run:[INDENT]sudo apt-get install python libusb-dev ppp python-usb[/INDENT]That command installs the python, pppd, libusb and the python usb(pyusb) modules, which are needed to run the bbtether program.

Then I needed to run:[INDENT]sudo apt-get install python-wxgtk2.8[/INDENT]That command installed the graphical version of python, which I believe is only needed if you want to run the graphical version of bbtether.

Next I needed to download the bbtether package:
[http://www.colar.net/websvn/filedetails.php?repname=src&path=%2Fbbtether%2Fbbtether.tgz](http://www.colar.net/websvn/filedetails.php?repname=src&path=%2Fbbtether%2Fbbtether.tgz)
Put the file in a folder and then extract the files from the archive.  I used the file browser and then right clicked on the file and chose the "Extract Here" option.  I'm a newbie so I'm not sure where the best place to put these files are.  I put mine in my user's home directory.  Are there any suggestions on a better place to put the files?  If I put them in my personal directory then am I keeping other users from being able to access them?

Now that everything is installed, it's time to run the program.  Since I don't know if my PPPD supports "replacedefaultroute", I followed the steps to disable my other network interfaces (eg. wifi)
Open a terminal window and run:[INDENT]route[/INDENT]Look at the output and it will list the interfaces.  Mine was "eth1"

Next, bring down that interface:[INDENT]sudo ifconfig eth1 down[/INDENT]replace eth1 with your interface.  I don't know if you need to bring down any other interfaces if you have them running.

Now you can run the bbtether program.  In the terminal window, go to the bbtether directory and run:[INDENT]sudo ./berry4all.sh[/INDENT]That will bring up the Berry4All graphical interface.  Then choose "Modem" and "Connect".  That will ask you for you BlackBerry password (if you have one) and which script you want to use.

Once you are done, you will need to disconnect (hang up) the modem by choosing "Modem" and "Disconnect".  This will run another script that you should give a few seconds to complete before exiting Berry4All.

The final step is very important, and it didn't work for me.  You will now need to re-enable your other connections. (eg. wifi)  To do this you will need to run:[INDENT]sudo ifconfig eth1 up [/INDENT]and possibly:[INDENT]sudo /etc/init.d/networking restart[/INDENT]The wifi didn't come back up for me, so I just restarted the machine and it was back to "normal."

I hope this post helps some of the other newbies like me!


i'm trying to write the script and it says: was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

i'm not sure how to do this . do you have any ideas?:P

---

### Post by steveneddy on 2009-08-30
> **ceece said:**
> i'm trying to write the script and it says: was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

i'm not sure how to do this . do you have any ideas?:P

Simply copy and paste in a terminal:

```
sudo dpkg --configure -a
```

which is precisely what it told you to do.

---

### Post by ceece on 2009-08-30
> **steveneddy said:**
> Simply copy and paste in a terminal:
 
```
sudo dpkg --configure -a
```
 
which is precisely what it told you to do.
 
 
Thanks, Sorry I am totally so stupid and new to  and working with Linux system. I didn't know what "manually run" meant. :confused:
But hey, I guess we all gotta start somewhere!! :)

---

### Post by BrandonBan6 on 2009-09-23
Thanks for posting this, works great!

I wrote a bash that launches my vpn client and berry! Loving Linux!

---

### Post by mohnkern on 2009-09-29
Yes, putting them in your home directory is likely to make them so other users can't use them (It depends on the permissions of your home directory, and the directory where you put the files.

I'd be inclined to put them in /usr/local/bin/btether, or if you want to be "old school" you put them in /opt/btether.

You'll need to sudo when you put the files in, and you'll want to make sure that the permissions are sufficient for all users to read and execute the necessary files.

Then again, it always depends upon how your computer is being used.  There are a lot of Ubuntu installs where  there is only one user account, so putting them in ~/bin/btether may make sense, and keeping the ownership to your user name makes sense as well.

> **st8ofmi9d said:**
>  I used the file browser and then right clicked on the file and chose the "Extract Here" option.  I'm a newbie so I'm not sure where the best place to put these files are.  I put mine in my user's home directory.  Are there any suggestions on a better place to put the files?  If I put them in my personal directory then am I keeping other users from being able to access them?



---

### Post by mohnkern on 2009-09-29
Has anyone resolved the issue with Wifi not coming up after doing this?  (without rebooting).

---

### Post by gear.h34d.2012 on 2010-04-06
Any possible way to do this via Bluetooth?

---

### Post by B34N on 2010-04-07
> **gear.h34d.2012 said:**
> Any possible way to do this via Bluetooth?

I have not seen a way but it you figure it out, please post a response.

FYI: It will not connect if your phone is set to 3G. I set my Bold 9700 to 2G, connect and then switch to 3G and I get 3G speeds.

---

### Post by Bashar &quot; on 2010-04-25
what if my carrier is not listed between the configs available ? i'm trying to tweak vodafone's as it used to work for my carrier (Zain)

---

### Post by thync on 2010-05-05
I'm running 9.10 and my phone's a BB Curve 8520. Will this method of tethering take advantage of BB's BIS (i.e., free internet access)?

---

### Post by xt8088 on 2010-08-16
> **Bashar " said:**
> what if my carrier is not listed between the configs available ? i'm trying to tweak vodafone's as it used to work for my carrier (Zain)

For Zain in Tanzania, try these

Both need to be placed in the conf directory of bbtether.  It is working for me on 10.04!

PS. I'm posting while tethered

---

### Post by Bashar &quot; on 2010-08-16
> **xt8088 said:**
> For Zain in Tanzania, try these

Both need to be placed in the conf directory of bbtether.  It is working for me on 10.04!

PS. I'm posting while tethered
i get "Invalid Attachment specified. If you followed a valid link, please notify the administrator" when i try to download the file

can you please upload it again ? :)

Thanksin advnace

---

