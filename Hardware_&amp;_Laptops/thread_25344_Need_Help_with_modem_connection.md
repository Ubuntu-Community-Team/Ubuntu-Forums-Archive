---
title: "Need Help with modem connection"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by jozmak on 2005-04-09
Hi,
I updated to hoary and everything went fine except that I cannot connect to the internet anylonger. In wharty it was a smooth sailing. I used pppconfig and it worked like charm. But it doesn’t work with hoary.
I have an external robotics modem and while trying to connect the log file gives me the following message

pr  9 21:21:42 localhost pppd[6993]: pppd 2.4.2 started by root, uid 0
Apr  9 21:21:43 localhost chat[6994]: abort on (BUSY)
Apr  9 21:21:43 localhost chat[6994]: abort on (NO CARRIER)
Apr  9 21:21:43 localhost chat[6994]: abort on (VOICE)
Apr  9 21:21:43 localhost chat[6994]: abort on (NO DIALTONE)
Apr  9 21:21:43 localhost chat[6994]: send (ATZW2^M)
Apr  9 21:21:43 localhost chat[6994]: expect (OK)
Apr  9 21:21:43 localhost chat[6994]: ATZW2^M^M
Apr  9 21:21:43 localhost chat[6994]: OK
Apr  9 21:21:43 localhost chat[6994]:  -- got it
Apr  9 21:21:43 localhost chat[6994]: send (ATDT<put^M)
Apr  9 21:21:43 localhost chat[6994]: expect (phone)
Apr  9 21:21:43 localhost chat[6994]: ^M
Apr  9 21:22:28 localhost chat[6994]: alarm
Apr  9 21:22:28 localhost chat[6994]: Failed
Apr  9 21:23:01 localhost chat[7009]: abort on (BUSY)
Apr  9 21:23:01 localhost chat[7009]: abort on (NO CARRIER)
Apr  9 21:23:01 localhost chat[7009]: abort on (VOICE)
Apr  9 21:23:01 localhost chat[7009]: abort on (NO DIALTONE)
Apr  9 21:23:01 localhost chat[7009]: send (ATZW2^M)
Apr  9 21:23:01 localhost chat[7009]: expect (OK)
Apr  9 21:23:01 localhost chat[7009]: ATZW2^M^M
Apr  9 21:23:01 localhost chat[7009]: OK
Apr  9 21:23:01 localhost chat[7009]:  -- got it
Apr  9 21:23:01 localhost chat[7009]: send (ATDT<put^M)
Apr  9 21:23:01 localhost chat[7009]: expect (phone)
Apr  9 21:23:01 localhost chat[7009]: ^M
Apr  9 21:23:46 localhost chat[7009]: alarm
Apr  9 21:23:46 localhost chat[7009]: Failed

Help would be greatly appreciated.
jozmak

---

### Post by heimo on 2005-04-10
Ok.. This is hard for me to answer - haven't used modems for long time, but let's try to get this fixed! :)

Have you checked your settings System->Administration->Networking (Modem Connection->Properties)? If those are ok (you need to have phone number, username and password configured), you can check files in "/etc/chatscripts/" directory, files like 'provider' or 'ppp0' or something like that. That's called chatscript - the "discussion" your modem and internet service providers modem go through to establish connection. 

But I guess it should contain your settings from System->Administration->Networking->Modem Connection. Seems like you could be missing the phone number (??). It should be just after ATDT. It also could be problem with modem not getting dial tone. Check the cables (I'm sure you have already, but do it again.. if possible, try regular phone on the same line to check that line is ok).

You can try changing ATDT<your isp's phone number here>  command to ATX3DT<your isp's phone number here>, which should make your modem ignore dial tone and call the number anyway.

You can also try calling the ISP's number with voice phone just to check that the number is ok. If you need to use 0 or 9 to get outside, remember to add that also to your modem settings phone number.

Username and password from System->Administration->Networking->Modem Settings goes to file in '/etc/ppp/pap-secrets'. You should be able to install minicom (if that's not already installed) and run it from console or terminal and use same AT commands from the chatscript to debug your problem. (ATZ resets modem, ATDT<phone number> calls the phone number, ATX3 sets modem to ignore dial tone and so on). This way you can also make sure that the serial (?) connection to your modem is ok.

Hope this helps.

EDIT: Oh... :)

```
Apr 9 21:23:01 localhost chat[7009]: send (ATDT<put^M)

```

This is the line that caught my eye. I didn't emphasize it in my reply, but there should be number after ATDT and that <put^M part seems like text from unconfigured chatscript. (<put phone number here>)

---

### Post by jozmak on 2005-04-10
Hi heimo,

Thanks a lot for your help. Tomorrow I go over on your suggestions becouse it is very late here and I hardly see the monitor.

jozmak

---

### Post by jozmak on 2005-04-10
Hi heimo

I was up early in the morning and went through the issues you suggested yesterday. 
With the modem and telephone line don't seen anything wrong because i have a dual boot system and the modem works perfectly on XP.
I also looked into the /etc/chatscripts folder and opened all of the files and everything looks ok there. After the ATDT i see everywhere the telephone number. 
In the /etc/ppp folder i found three files namely chap-secrets, pap-secrets, and pap-secrets.bak which are marked a red icon with an x mark on them and file type unknown. I don't know there is any significance to these.
To day I tried to connect to the Internet using the Networking from the Administration menu. In fact, I could connect; however the connection is extremely slooooow, almost unusable. I takes 1-2 minutes to go from one page to the next. Normally, it takes a few seconds. On windows an average of 5 seconds and up until yesterday whary was even faster. 
The line you mentioned in your email that suppose to include a telephone number I couldn't figure in what file should I look at it. 

Thanks
jozmak

---

### Post by heimo on 2005-04-10
It's still the same day here. ;)

You could try these:

```

sudo setserial /dev/ttyS0 autoconfig
sudo setserial /dev/ttyS0 irq 0

```

Substitute ttyS0 with the actual serial port your modem is connected to. (you can see this in System->Administration->Networking->Modem connection->Modem->Modem port, or you can also try just /dev/modem, which should be symbolink link to the actual serial device - /dev/ttyS0 is "COM1" /dev/ttyS1 is "COM2".

The problem is not the phone number if the connection can be established, but is just slow. Could be hardware conflict (irq conflict), or misconfigured serial port. You can see more choices for setserial parameters if you run it without any parameters. If that program is not installed, do:
```
sudo apt-get install setserial

```

---

### Post by jozmak on 2005-04-10
Thanks for the new ideas. But now I am moving in a vicious circle. To install setserial program, first, i have to upgrade my source.list but when i try to do that i get the message  “Could not download all repository indexes because of networks problem” So when I try to install getserial of course, I get the message that the package is not found. 
The strangest thing to me in this connection saga is that what could cause the pppconf to fail. I remember when I installed wharty I followed the pppconf instructions on the ubuntu documentation page and it worked right away.  I tried repeatedly this on hoary  without luck. 

jozmak

---

### Post by heimo on 2005-04-10
:? I'm running out of ideas. You could try running
```
tail -f /var/log/messages
```
in terminal window while connecting / connected to internet. Watch for anything with ppp or ttyS or modem or IRQ ... or just anything suspicious. 

And you could also check
```
/sbin/ifconfig
```
and look at the ppp section for errors, dropped, overruns, collisions... compared to packets count.

:( I'm hoping the best.

---

### Post by jozmak on 2005-04-10
Hi heimo,

I have a good news. I was googling around and i came across a wvdial  documentation page. I copied a sample wvdial.conf file from the page and with that I created a new one for my computer. I replaced the telephone number, login and password section and now my computer back to its original connection speed. This is awesome. But I couldn't follow everything in the documentation because the page was outdated and some of the files it referred to do not exist on my computer. And because i have never used this tool before i don't know how to shut it off. For the time being i just turn off the modem but there should be a better way to do that. I also wonder, is there a graphical interface to wvdial tool. I tried to create a launcher to the usr/bin folder where the wvdial executable lives but nothing happens when i click on it. I also tried to download gnome-ppp but i cannot install it because of dependency problems.

Thanks
jozmak

---

### Post by heimo on 2005-04-10
Nice to hear your internet connection is now at least usable! :) Makes life a lot easier.

I tried to install gnome-ppp and it looks nice and clean interface to dialup connections. What kind of dependency problems are you having? Have you tried something like:

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install gnome-ppp

```

---

### Post by jozmak on 2005-04-10
when I try to update the list I get the following error message.

Fetched 571B in 15s (36B/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

And when i try to install gnome-ppp i get the following error.

root@ubuntu:/home/mak # apt-get install gnome-ppp
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gnome-ppp

Thanks
jozmak

---

### Post by jozmak on 2005-04-10
Now, i downloaded the gnome-ppp source file and when i configure, it complains about a missing xml:parser. But i have found no xml parser in the repository either.

---

### Post by jozmak on 2005-04-10
Hi heimo

This is the final solution. In the source list, I changed the Canadian addresses to us and updated the lists once again. This time all repository index downloaded properly. Then, I could install gnome-ppp. Now i have a nice graphical front end and everything works great. 
Thanks once again for taking the time and giving me excellent clues how to go about solving this nasty problem.

Regards
jozmak

---

### Post by N8MAN1068 on 2005-09-22
[QUOTE=jozmak]Hi heimo,

I have a good news. I was googling around and i came across a wvdial  documentation page. [/QUOTE]
got a link?

I know it's an old post, but links are helpfull when people like me spend time searching for stuff on forums.

---

