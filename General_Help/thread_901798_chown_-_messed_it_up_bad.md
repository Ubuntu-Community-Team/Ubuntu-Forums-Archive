---
title: "chown - messed it up bad"
date: 2008-08-26
forum: General Help
---

### Post by Ivalde on 2008-08-26
Hello everyone

One hour ago I just did one of these NO-NO things. Hopefully someone here could help me restore at least parts of this mess.

But first to the laughter in tears.

I was sitting and setting up a new local website on my 6.06 LTS server edition with xubuntu. I have these local websites stored on a separate hda3 and I was doing fine. Just needed to change owner on some directories. Alright, you are guessing where this is going....

Typed: $ sudo -R www-data:www-data / 
and instead of writing the rest of the path I pressed [Enter]
Yihaa!!! all files on my server is now owned by www-data *sick*

You do not have to tell me I am an idiot, I already know that. But if you would like to help a poor windows guy that is cheating with linux/ubuntu as good as he can... I´d be very happy.

This is what I have done:

1) Since sudo stopped working I was basically stuck. Rebooted the server and via grub and entered Recovery mode. Changed my /home directory to my username:users

2) Since I was in recovery mode I also chown:ed /root /sbin /var to root:root (sounded like a good idea)

3) Googled like a madman to get some advise and found an older advise here on the forum that indicated that I needed to change the sudo ownership and mod, which I did
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

3) Rebooted again and now I could login with my username again

4) opened a terminal window and thought maybe also /etc should be set to root:root. Used sudo chown -R root:root /etc/
Replay was:
"sudo: /etc/sudoers is owned by uid 33, should be 0"
Then the following message started:
"postdrop: warning mail_queue_enter: create file mauldrop/27048:5211: Permission denied"
and keep returning this message for 15 min just changing the 27048 to different numbers 

5) Rebooted again.

Basically, here I am. Have 30 min before I need to leave the house for a 2 days business trip (why does this always happens with bad timing Mr Murphy?).

I am (or was) running the server as fileserver (samba), mailserver and webserver (apache2). No special tailormade setup, did just follow the instructions and used default setup when I set this server up (only created virtual www paths to the secondary (hda3) where the websites are located, non of them are in production of course).

If anyone could help me (or point me in the direction) what I need to do to get this machine back in order (preferably not a re-install). All help very appreciated....

---

### Post by chrisccoulson on 2008-08-26
It might be possible to partly recover it if you're willing to put in quite a bit of effort, but IMO you would probably be better off doing a re-install (this might be the quicker option too).

---

### Post by Ivalde on 2008-08-26
Yes, you are probably right. Maybe it is time to upgrade to 8.04.

But to "survive" the next week or so, I really need to get the network connection, samba, apache2 and mySQL to work (starting with the network connection and samba so I can save all files since last backup). The comp is old, and have neither usb or a cd writer (but it works like a charm :) )

---

### Post by Ivalde on 2008-08-29
Have decided to try to do a short term rescue on the machine (if possible).

Have managed to get sudo going (by chown root:root and chmod 4411 /usr/bin/sudo ). Not sure why 4755 did not work, but now it works with 4411.
Have basically chown:en all / directories (/sbin /var etc) to root:root instead of www-data:www-data.

The machine is starting and loading xubuntu and everything looks ok during startup.
Synaptics works - good
Re-installed DHCP-package: The network started to working again without manual config - very good
Samba is up and running, so I can access all docs from the network - good

Re-installed postfix: The imap connection from my windows machins can connect - good
Re-installed fetchmail: Seems to run but do not fetch any mail (setup is to collect incoming pop-mail)

Apache2 running and simple sites works 
Joomla based sites does not work which I assume is related to mySQL

If anyone have advise on what essential files needs to be changed from owner root:root to get my SQL to work it would be very appreciated.

---

