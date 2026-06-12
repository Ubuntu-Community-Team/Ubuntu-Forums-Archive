---
title: "Installing 3ware 3DM"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by prodsacnetworking on 2006-09-22
Hi,

I have a mail server running Ubuntu 6.06 Server.
Its a Dell PowerEdge 850 with 2 X Seagate 500Go plugged on a 3Ware 9550SX in Raid-1.

It runs fine. But I can't seem to install the Monitoring, web accessible, 3DM2 software.

Any input on that? 

Thanks a lot ;-)

---

### Post by piers on 2006-10-18
Anybody?

I've tried installing the port from debian-unofficial but that doesn't work either. it opens port 888 but it doesn't respond ](*,) 

I have it running successfully on another (older) ubuntu machine but can't remember how I did it.

---

### Post by Streborekul on 2006-11-24
> **piers said:**
> Anybody?

I've tried installing the port from debian-unofficial but that doesn't work either. it opens port 888 but it doesn't respond ](*,)

Are you sure that is not a firewall rule blocking port 888? (I had a simular problem once when instlling from ports on FreeBSD). 

I have the 3ware 9550Xs card installed on Ubuntu Edgy, but can't find how to install 3DM monitoring at all. 
You mention you installed it from Debian unofficial...? Any tips?

> **piers said:**
> 
I have it running successfully on another (older) ubuntu machine but can't remember how I did it.

I (and I'm sure many others) would be VERY happy if you would remember.

Thanks,

Streborekul

---

### Post by prodsacnetworking on 2006-11-24
Ok, cool.

I did'nt knew this trick.

you add: 
# Debian Unnoficial
deb [http://ftp.debian-unofficial.org/debian](http://ftp.debian-unofficial.org/debian) stable main contrib non-free restricted

to the sources-list apt file.
apt-get update

you can search through the repository

---

### Post by piers on 2006-11-27
Good grief, after all this time it was my local firewall stopping access!! My other machines have 3dm2 set up on a different port! :KS

---

### Post by Streborekul on 2006-11-30
Seems like we all just helped each other! 

I just got 3dm2 running (on Ubuntu Edgy 32bit) thanks to the 'unofficial debian' addition to my sources list apt file (in /etc/apt/). 

For you guys out there wondering how..? 

After I modified my sources list, I used 'synaptics' from the terminal. There in one of the sections, I saw the 3dm2 utility... As I had not supplied a key for the unofficial debian list, Synaptics asked me if I was sure if I trusted the source. After I gave permission, the installation went and in a screen I was asked to guide the installation. After that, a simple 3dm2 comand was enough to start the utility. 

Thanks!

---

### Post by Noxid on 2007-01-25
I added the

# Debian Unnoficial
deb [http://ftp.debian-unofficial.org/debian](http://ftp.debian-unofficial.org/debian) stable main contrib non-free restricted

to the sources-list apt file.

but how do I install it from a command line? I have a server install and don't have a graphical interface.

Thanks.

---

### Post by sanitycheck on 2007-02-28
@noxid: You want to use the shell program called aptitude.  Lots of information out there how to use it.  I'm old school so use it instead of Adept (or whatever it's called) in KDE.
---
Is there a way (an easy way) to pull just the 3DM package from the debian-unofficial package list, instead of everything listed under restricted?  I'd rather not add any other packages from debian-unofficial to avoid any conflicts with packages in other repositories.  I guess I could just install the deb manually but I would rather retain the auto-update feature of pulling from a repository.

I must say I am rather surprised and disappointed to see so little information about, and direct support for, 3DM under (k)ubuntu, considering the wide acceptance of 3ware's controllers under Linux.  I used 3DM on a Debian Woody/Sarge box for years, and installing it was no problem.  The 3Ware controllers are great but 3DM is a critically important piece of the puzzle.  

I recently lost a drive on a new RAID5 setup, but didn't know it until I noticed a major slow-down.  I had to reboot the machine to learn what happened.  I now reboot the box every few days to see if the rebuilt array is staying up.  This isn't exactly what I had in mind when I set the box up.

- thanks in advance for any help

---

### Post by Holzmann on 2007-03-25
I just bought a 3ware 8006-2LP PCI SATA RAID card.

It is up and running Ubuntu SERVER 6.10 in RAID 0. 

I would appreciate step-by-step instructions on how to install the 3DM/Web-based monitoring utility.

Thank you!

---

### Post by rogblake on 2007-03-25
> **sanitycheck said:**
> 
I recently lost a drive on a new RAID5 setup, but didn't know it until I noticed a major slow-down.  I had to reboot the machine to learn what happened.  I now reboot the box every few days to see if the rebuilt array is staying up.  This isn't exactly what I had in mind when I set the box up.


I have also had problems getting the 3DM web-based monitor to work properly on various Linux servers. However, 3Ware also provides a CLI tool which can be used to check the array status. I run a shell script periodically via cron that checks for trouble, logs status via syslog, and emails the system administrator(s) if an error condition exists. (Obviously for email to work, the server must have a properly configured MTA running.) It's a crude approach but it works, the scipt is attached.

---

### Post by Holzmann on 2007-03-26
> **rogblake said:**
> I have also had problems getting the 3DM web-based monitor to work properly on various Linux servers. However, 3Ware also provides a CLI tool which can be used to check the array status. I run a shell script periodically via cron that checks for trouble, logs status via syslog, and emails the system administrator(s) if an error condition exists. (Obviously for email to work, the server must have a properly configured MTA running.) It's a crude approach but it works, the scipt is attached.

I am really a beginner when it comes to this stuff.

Could you please provide step-by-step instructions on how to un-zip, install, etc. from a command line interface?

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> I am really a beginner when it comes to this stuff.
Could you please provide step-by-step instructions on how to un-zip, install, etc. from a command line interface?

There is not a lot to it. All of the following things need to be done from the root account, so if you have activated root, log in that way or use 'su,' otherwise you will need to prepend 'sudo' to all of the commands you run.

Install the CLI either from the driver disc provided with the controller, or download from the 3Ware web site. (They should have specific instructions, I don't recall off the top of my head but the CLI tools probably are in a tarball that you would unpack with a command similar to 'tar zxvf cli_tools.tar.gz.') You would probably want the CLI files to wind up in someplace like /usr/local/bin or /usr/local/sbin.

You would then place the checkraid.sh file in some convenient place (I have it in /root/bin, but it could just as well go into /usr/local/bin or whatever), and modify it to suit local conditions. If you have only a single controller and array the 'tw_cli' command should not need to be modified, you would only need to change the e-mail address(es) to suit. 

The shell script as currently written only sends email if a degraded array is found, but it would be a simple modification to have it send email to confirm proper operation. (You would just add the appropriate 'mail' command to the 'else' section.)

Then it's just a matter of setting up a cron job to run the script periodically. The command 'man cron' will give you the basics, but essentially you would run the command 'crontab -e' which brings up the crontab file in the vi editor. Add an entry similar to the following, which runs the array check every day at 5:00 AM:

0 5 * * * /bin/sh /root/bin/checkraid.sh > /var/log/checkraid.log 2>&1

Obviously you would want the path to the checkraid.sh script to match wherever you put the file. That's about it. You can grep /var/log/messages for 'checkraid' to see messages that get put in the system log file, wait for e-mail messages,  or run checkraid.sh any time from the command line to check the array status.

---

### Post by Holzmann on 2007-03-26
Does this look like the correct file to download?

[http://www.3ware.com/support/download_9.3.0.7.asp](http://www.3ware.com/support/download_9.3.0.7.asp)

---

### Post by Holzmann on 2007-03-26
When I un-tar the file, I get:


tw_cli
tw_cli.8.html
tw_cli.8.nroff
tw_sched
tw_sched.8.html
tw_sched.8.nroff
tw_sched.cfg

So you're saying place all these in /usr/local/bin for example?

I really do not care about the e-mail function. Just a quick summary of status at the command line is fine with me.

Which of the above files do I run? And how do I run it? ./tw_cli ?

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> When I un-tar the file, I get:

tw_cli
tw_cli.8.html
tw_cli.8.nroff
tw_sched
tw_sched.8.html
tw_sched.8.nroff
tw_sched.cfg

So you're saying place all these in /usr/local/bin for example?

I really do not care about the e-mail function. Just a quick summary of status at the command line is fine with me.

Which of the above files do I run? And how do I run it? ./tw_cli ?

All you really need is the 'tw_cli' file, which is the executable, place that in /usr/local/bin. The tw_sched is for features which are only in some 3Ware controllers, but you don't need it to check status. The '.8' files are documentation, that is, man pages. If you are not accustomed to working from the command line, the easiest thing to do is put tw_cli.8.html in some convenient directory to open up in your favorite web browser in order to review the documentation.

To check that tw_cli works, run the command line found in the checkraid.sh file. (That is, run 'tw_cli /c0/u0 show') and if all is working properly it will give you the status of your array. If /usr/local/bin is in your search path it is not necessary to give the full path to the executable.

If you are not interested in email notification and just want a quick check from the command line, the simplest thing to do is instead of using the shell script and cron just make an alias by putting something like "alias checkraid='tw_cli /c0/u0 show'" in your .bashrc file.

---

### Post by Holzmann on 2007-03-26
> **rogblake said:**
> All you really need is the 'tw_cli' file, which is the executable, place that in /usr/local/bin. The tw_sched is for features which are only in some 3Ware controllers, but you don't need it to check status. The '.8' files are documentation, that is, man pages. If you are not accustomed to working from the command line, the easiest thing to do is put tw_cli.8.html in some convenient directory to open up in your favorite web browser in order to review the documentation.

To check that tw_cli works, run the command line found in the checkraid.sh file. (That is, run 'tw_cli /c0/u0 show') and if all is working properly it will give you the status of your array. If /usr/local/bin is in your search path it is not necessary to give the full path to the executable.

If you are not interested in email notification and just want a quick check from the command line, the simplest thing to do is instead of using the shell script and cron just make an alias by putting something like "alias checkraid='tw_cli /c0/u0 show'" in your .bashrc file.

Okay, so I still need to download that script you attached. Or instead of that just design an alias as you put it.

So here are the steps:

1) Move tw_cli to /usr/local/bin
2) Open .bashrc and add the alias. (Where is this file located?)
3) From the command line, type: checkraid (Is that all?)

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> Okay, so I still need to download that script you attached. Or instead of that just design an alias as you put it.

So here are the steps:

1) Move tw_cli to /usr/local/bin
2) Open .bashrc and add the alias. (Where is this file located?)
3) From the command line, type: checkraid (Is that all?)

You don't need the script if all you want to do is to check the array status from the command line. Strictly speaking you don't need the alias either, just makes for something easier to remember.

Your .bashrc file is in your home directory. If you add the following to it, you should be able to check your RAID status by just entering the command "checkraid"...

  alias checkraid='/usr/local/bin/tw_cli /c0/u0 show'

(Note that you need to either log out and back in, or enter the command "source .bashrc" to reload the .bashrc file.)

---

### Post by Holzmann on 2007-03-26
Okay, so as root I moved tw_cli to /usr/local/bin, switched to user and added the alias line to that user's .bashrc file. I restarted the .bashrc file and of course got this error:

bash: /usr/local/bin/tw_cli: Permission denied.

I cannot move tw_cli from my home directory to /usr/local/bin as user. I must be root, yes?

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> Okay, so as root I moved tw_cli to /usr/local/bin, switched to user and added the alias line to that user's .bashrc file. I restarted the .bashrc file and of course got this error:

bash: /usr/local/bin/tw_cli: Permission denied.

I cannot move tw_cli from my home directory to /usr/local/bin as user. I must be root, yes?

You need to be root to move the tw_cli file to /usr/local/bin. You may also need to be root to run that program, I don't know that I've ever tried it logged in as a regular user. You can try setting permissions on the file (chmod 775 /usr/local/bin/tw_cli), but even if you can execute the program that doesn't mean it will work from a non-privileged account.

---

### Post by Holzmann on 2007-03-26
When I run "checkraid" as root, I get

**-bash: checkraid: command not found**

The bash file I edited was in /home/user/.

Does this mean I need to find the bash file for root instead?

Edit: Here are the current conditions on the file in /usr/local/bin/:

**-rwxr--r-- 1 root root 1871620 2007-03-26 12:39 tw_cli**

---

### Post by Holzmann on 2007-03-26
I just ran ./tw_cli from /usr/local/bin and it runs. I get:

Ctl   Model        Ports   Drives   Units   NotOpt   RRate   VRate   BBU
------------------------------------------------------------------------
c0    8006-2LP     2       2        1       0        2       -       -

So it works.

The alias at the moment does not.

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> When I run "checkraid" as root, I get

**-bash: checkraid: command not found**

The bash file I edited was in /home/user/.

Does this mean I need to find the bash file for root instead?

Edit: Here are the current conditions on the file in /usr/local/bin/:

**-rwxr--r-- 1 root root 1871620 2007-03-26 12:39 tw_cli**

As far as the alias, yes, you need to edit the file /root/.bashrc for root to pick up your new alias. Check that you have the correct path to the tw_cli file, and you need to log out and back in again (or run "source .bashrc") to re-read your configuration. A sure-fire way to do this, of course, is to reboot. though it is overkill. You could also just try running the tw_cli command ("tw_cli /c0/u0 show") to see if it works without worrying about the convenience of an alias for the moment.

BTW, with those permissions, only root will be able to execute the file. You need to "chmod 755 /usr/local/bin/tw_cli" to make the file executable by others. (Though obviously if it needs root permissions to obtain the array status, it will not work if run by anyone else but root.)

---

### Post by Holzmann on 2007-03-26
Okay, it all works now. 

I run **checkraid** at the command line and get:

Unit     UnitType  Status         %Cmpl  Port  Stripe  Size(GB)  Blocks
-----------------------------------------------------------------------
u0       RAID-1    OK             -      -     -       465.761   976771120
u0-0     DISK      OK             -      p0    -       465.761   976771120
u0-1     DISK      OK             -      p1    -       465.761   976771120

Since the stripe size is only the size of half the total capacity I assume that it is indeed running in RAID 0, not RAID-1 as it says under Unit Type.

---

### Post by Holzmann on 2007-03-26
Rogblake: Thank you so much for your patience and input.

The 3DM web utility would be nice but I think this is good enough. I just want to be able to check from time to time that the drives are running okay.

---

### Post by rogblake on 2007-03-26
> **Holzmann said:**
> 
...
Since the stripe size is only the size of half the total capacity I assume that it is indeed running in RAID 0, not RAID-1 as it says under Unit Type.

Actually the display is correct, with RAID-1 you lose half your total capacity as the data is mirrored across the two disks. RAID-0 would give you full capacity but no fault tolerance. (Lose one drive with RAID-0 and you're hosed.) Glad it's working for you!

---

### Post by Holzmann on 2007-03-28
Another question:

Would there be an "easy" way of getting the results of "checkraid" (see below) to "print" inside a simple index.html file? A crontab could run the program like once an hour, get the text results and put into an index.html file. Perhaps that is what your script already does?



Unit     UnitType  Status         %Cmpl  Port  Stripe  Size(GB)  Blocks
-----------------------------------------------------------------------
u0       RAID-1    OK             -      -     -       465.761   976771120
u0-0     DISK      OK             -      p0    -       465.761   976771120
u0-1     DISK      OK             -      p1    -       465.761   976771120

---

### Post by Holzmann on 2007-03-28
So far I have:

**00,15,30,45 * * * * echo `/usr/local/bin/tw_cli /c0/u0 show` > /var/www/status.html **

But the formatting is still off.

---

### Post by rogblake on 2007-03-31
You need to wrap your tw_cli command in a script that will output some simple HTML formatting tags before and after the command's output. You would want your HTML file to wind up  look something like:

<html>
<pre>
... tw_cli ouput ...
</pre>
</html>

---

### Post by entirenet on 2007-06-01
Hi folks,

i have some problems with the tw_cli tool. I can start it from shell but it only reports:

---

[B]root@scmhost:~# ./tw_cli 
3ware CLI> ?

Copyright (c) 2003 3ware, Inc.  All rights reserved.
3ware CLI (version 2.00.00.032b)


Commands   Description
-------------------------------------------------------------------
info       Displays information about the controller
alarms     Displays or deletes the list of AENs
set        Displays or modifies controller settings
maint      Performs maintenance operations on a controller
quit       Exits the CLI

Type help <command> to get more details about a particular command.

3ware CLI> info
List of controllers
-------------------
No controller found.
Make sure appropriate 3Ware device driver(s) are loaded.
3ware CLI> [/B]

---

How can i make sure that the appropriate 3Ware drivers are loaded? I am using Ubuntu 7.04 as  i386 server edition and the raid-1 currently works great without installing any special driver.

I am using an 3ware 8006-2LP PCI SATA RAID card just as in Holzmann's case...

Any hints?

thx

entirenet

---

### Post by cmdln on 2007-06-06
> **Holzmann said:**
> I just bought a 3ware 8006-2LP PCI SATA RAID card.

It is up and running Ubuntu SERVER 6.10 in RAID 0. 

I would appreciate step-by-step instructions on how to install the 3DM/Web-based monitoring utility.

Thank you!

tw_cli is their commandline utility. Its pretty decent

tw_cli info

then /cx show
where /cx is your controller

like so .... then just stick that in something and have the output emailed to you every night. Even better grep for the status you expect and if its not there send an email to you.
```

debian:~# tw_cli info    

Ctl   Model        Ports   Drives   Units   NotOpt   RRate   VRate   BBU
------------------------------------------------------------------------
c4    9650SE-12ML  12      6        2       1        5       5       -        

debian:~# tw_cli /c4 show

Unit  UnitType  Status         %Cmpl  Stripe  Size(GB)  Cache  AVerify  IgnECC
------------------------------------------------------------------------------
u0    RAID-5    INITIALIZING   14     64K     1862.61   OFF    OFF      OFF      
u1    SPARE     OK             -      -       465.753   -      OFF      -        

Port   Status           Unit   Size        Blocks        Serial
---------------------------------------------------------------
p0     OK               u0     465.76 GB   976773168     9QG0DLWR            
p1     OK               u0     465.76 GB   976773168     9QG0D5JB            
p2     OK               u0     465.76 GB   976773168     9QG0CC5M            
p3     OK               u0     465.76 GB   976773168     9QG0DLQ9            
p4     OK               u0     465.76 GB   976773168     9QG0BHEE            
p5     OK               u1     465.76 GB   976773168     9QG0CTXH            
p6     NOT-PRESENT      -      -           -             -
p7     NOT-PRESENT      -      -           -             -
p8     NOT-PRESENT      -      -           -             -
p9     NOT-PRESENT      -      -           -             -
p10    NOT-PRESENT      -      -           -             -
p11    NOT-PRESENT      -      -           -             -


```


--
[http://anders0n.net](http://anders0n.net)

---

### Post by cmdln on 2007-06-06
> **entirenet said:**
> Hi folks,

How can i make sure that the appropriate 3Ware drivers are loaded? I am using Ubuntu 7.04 as  i386 server edition and the raid-1 currently works great without installing any special driver.

I am using an 3ware 8006-2LP PCI SATA RAID card just as in Holzmann's case...

Any hints?

thx

entirenet

tw_cli might only be for the 9000 series. 

I couldnt find any information on 8000 series specifically but my guess is your going to need to find the older cli_linux utility.  Check 3wares website.

--
[http://anders0n.net](http://anders0n.net)

---

### Post by icpeanuts on 2007-06-15
I was able to download the 3dm2, installed and it works fine.

Here is the link
[http://ftp.debian-unofficial.org/debian/pool/restricted/3/3ware-3dm2-binary-i386/](http://ftp.debian-unofficial.org/debian/pool/restricted/3/3ware-3dm2-binary-i386/)

Double click and install the package. Went to terminal, ran sudo 3dm2 status

Open Firefox
[https://localhost:888/](https://localhost:888/)

Went thru few security mumble jumbo.

I am at the 3dm2 login page.

Default password is: 3ware.

The web tool is pretty nice. I wish there is a section for sending email authenication since I do not have mail server daemon setup on this box. 

Hope this help.

---

### Post by Martin Macleod on 2007-06-25
Thanks icpeanuts, that got my 3dm2 web monitoring working :)

---

### Post by yurtboy on 2007-07-30
this really seems to work well.
Thanks
Alfred Nutile

---

### Post by neptho on 2007-09-23
As an alternative (command line only) availbility, I've found [these cli tools to be useful](http://jonas.genannt.name/). with an inherited system which has a 8006-2LP card.

Here are links to the latest [x86_64](http://jonas.genannt.name/3ware-cli-binary_9.4.1.2-1duo1_amd64.deb), and [i386](http://jonas.genannt.name/3ware-cli-binary_9.4.1.2-1duo1_i386.deb) versions.

This simple little utility gives you a decent overview, and allows you to rebuild, as well as most other tasks you'd do through a browser. 

I've made a little startup script to call the tw_cli program to turn on write cache for the controller with each reboot, and give me some simple status.  I've saved it as /etc/init.d/3warecache, and enabled the 'standard' way with 'update-rc.d 3warecache defaults.'  You will want to find your proper controller and unit, as shown in the example below:

```
# tw_cli show

Ctl   Model        Ports   Drives   Units   NotOpt   RRate   VRate   BBU
------------------------------------------------------------------------
c0    8006-2LP     2       2        1       0        2       -       -

# tw_cli /c0 show

Unit  UnitType  Status         %RCmpl  %V/I/M  Stripe  Size(GB)  Cache  AVrfy
------------------------------------------------------------------------------
u0    RAID-1    OK             -       -       -       111.79    ON     -

Port   Status           Unit   Size        Blocks        Serial
---------------------------------------------------------------
p0     OK               u0     111.79 GB   234441648     5MT3BA4S
p1     OK               u0     111.79 GB   234441648     5MT3BNZY

# tw_cli /c0/u0 show

Unit     UnitType  Status         %RCmpl  %V/I/M  Port  Stripe  Size(GB)
------------------------------------------------------------------------
u0       RAID-1    OK             -       -       -     -       111.79
u0-0     DISK      OK             -       -       p0    -       111.79
u0-1     DISK      OK             -       -       p1    -       111.79
```

```
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
CMD=/usr/sbin/tw_cli
#Insert your controller and proper array below.
#You can find this with tw_cli.
CONTROLLER=/c0
UNIT=u0

case "$1" in
  start)
    echo -n 'Turning on RAID write cache...'
    $CMD "$CONTROLLER/$UNIT set cache=on" >> /dev/null
    if [ $? -ne 0 ] ; then
      echo "failed."
      exit 1
    else
      echo "OK."
    fi
  ;;
  stop)
    echo -n 'Turning off RAID write cache...'
    $CMD "$CONTROLLER/$UNIT set cache=off" >> /dev/null
    if [ $? -ne 0 ] ; then
      echo "failed."
      exit 1
    else
      echo "OK."
    fi
  ;;
  restart|force-reload)
    $0 stop
    $0 start
  ;;
  diskstatus)
    echo "Disk Status"
    echo "-----------"
    #Ick, this should be done better, but I'm lazy
    $CMD "$CONTROLLER/$UNIT show" | awk "/$UNIT-/" | awk '{ print $1"\t"$3}'
  ;;
  status)
    $CMD "$CONTROLLER show"
  ;;
  *)
    echo "Usage: $0 {start|stop|restart|diskstatus|status}" >&2
    exit 1
  ;;
esac
exit 0
```

---

### Post by mozkill on 2007-12-07
> you add:
# Debian Unnoficial
deb [http://ftp.debian-unofficial.org/debian](http://ftp.debian-unofficial.org/debian) stable main contrib non-free restricted
to the sources-list apt file.
apt-get update
you can search through the repository
Default password is: 3ware.

thank you so much for that!

---

### Post by sanitycheck on 2008-02-10
The links Neptho provided give a nice list of 3DM-2 debs to download, which are apparently the same ones used on debian-unofficial.  

[http://jonas.genannt.name/]("http://jonas.genannt.name/")

I didn't want to add the entire debian-unoffical repository and dirty up my sources.list, so I installed the latest deb from there manually.  I also wanted the web version, not the CLI version.

I downloaded what appears to be the most current version of 3DM-2, which today was 3ware-3dm2-binary_9.5.0-1duo1_i386.deb.  I installed this package using gdebi (instead of dpkg), which helps make sure the dependencies are met.  

   gdebi 3ware-3dm2-binary_9.5.0-1duo1_i386.deb

Earlier I had manually checked to see if openssl was already installed (it was) with Adept.  Of course gdebi has to be installed to use it.

The package installed and works almost perfectly.  The only problem I have is that 3DM2 dies if I try to send a test alert email message.  It saves my email settings OK but only the test message doesn't work.  I emailed the package maintainer about the problem but didn't get a reply yet.  I tried to install one version earlier (3ware-3dm2-binary_9.4.1.2-2duo1_i386.deb), but it warned me that a newer version of the program was already installed.  I'm not going to uninstall the current version because it's not that big of a deal, but other people may want to try older versions first in case this is a bug in the latest version.

For reference I have:
Kubuntu 7.10 i386
3Ware 7006-2, stock 3Ware drivers, pair of 300 Gb Seagates set for RAID1

---

### Post by SFdrifter on 2008-03-07
To pick up where sanitycheck left off, I have the same problem using 9.4.13 under Gutsy:  I can configure the email settings, but a test email (and presumably an email generated by an error) locks up 3dm2 (and the email never arrives).

Any ideas what the solution might be?  Thx...

---

### Post by sanitycheck on 2008-03-10
Now we know the problem is not unique to the 9.5.0.1 version.  Unfortunately the package maintainer never responded to my email about this problem.

The next question is:  Does the warning email feature actually work, even though the test email feature crashes and kills 3DM2?  I'm hoping 3DM2 doesn't just die as soon as you have a problem and it tries to send an email.

---

### Post by konbaasiang7558 on 2008-04-12
Howdy!

I've got the same problem in Ubuntu 7.10 (amd64). Running 3dm2 works, but it crashes if I try to send a test e-mail.

Running two controllers (one 9500s-12mi and one 9500s-8) but this doesn't seem to be related, since others were having the same problem in other configurations.

The e-mail feature is really the only reason why I need 3dm2 in the first place. Does anyone have any solutions or ideas?

---

### Post by konbaasiang7558 on 2008-04-14
:popcorn:

GOT IT!

Problem solved.

I found the answer in the 3ware knowledge base:

Specify the IP address of the SMTP server, NOT the host name.

If you specify the IP address, it works like a charm.

Just thought you guys might like to know of this workaround. ;)

---

### Post by SFdrifter on 2008-04-19
Thx -- that gets me to the next 3dm2 email problem:  SMTP authorization failure.  D'oh!

Did you have an email program already installed on Ubuntu, or did you install and configure exim4 (I've read that there are a few exim configuration tweaks that can solve 3dm2's SMTP inadequacies), or did it just work?

---

