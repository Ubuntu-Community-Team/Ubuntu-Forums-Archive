---
title: "xubuntu and bluetooth GPS"
date: 2011-01-17
forum: Hardware
---

### Post by Keybored67 on 2011-01-17
Hoping this is the best place for this.

Ive been messing around with getting GPS running on xubuntu for a few days now and thought Id do a write up on how I did it.


Xubuntu comes with the bluez package installed, my bluetooth antenna is the Holux M-1000

There are more steps than would seem necessary, but after messing around with it for a couple days, this is the least amount of steps Ive been able to do to get it working.

In a terminal

$ sudo apt-get install gpsd-clients


I was having to stop and restart gpsd for some reason to get it to work, so I changed this file  /ect/default/gpsd  

START_DAEMON="false"

the rest of the file I left unchanged.


In a terminal

$ hcitool scan

copy the mac address of your bluetooth device, then type in

$ sdptool browse ##:##:##:##:##:##

that will spit out some info, the part you need is the channel number. The #'s is the mac address.

Then edit  ect/bluetooth/rfcomm.conf  by adding the following to the end of the file:

rfcomm4{
bind yes;
device ##:##:##:##:##:##;
channel #;
comment "GPS";
}



making the rfcomm connection wanted a password so I changed the permissions in the terminal 

sudo chmod 6755 /usr/bin/rfcomm



Now to run and test, the only way Ive been able to get it run is to do the following in two different terminals.  These are the steps that have to be done everytime I want to run anything GPS.

first terminal:

$ rfcomm connect 4
then hit ctrl c, to stop the connection, then re enter
$ rfcomm connect 4

why I need to start the connection, end it then restart it, I dont know.



Leaving that terminal open, open a second one and enter:

$ gpsd /dev/rfcomm4



Now to test to see if its all working type xgps in that second terminal.  If everything is as it should be, you will see data and satellite positions in a couple of seconds, depending if you can pick them up where your bluetooth antenna is. Now you can install and set up the mapping program of your choice. I only use xgps to make sure Ill be able to get data to a mapping program.

There maybe a better way to do all of this, open to suggestions on a better way, but this is the easiest Ive been able to come up with so far.  I would like to write a script with one icon on the desktop to click and it will start the bluetooth connection, start gpsd and start my mapping program.  The things I see in the way of that is the start stop restart of the rfcomm connection and having to have that first terminal window open.  Maybe getting that to run in the background or at least having it auto minimize to the task bar would be ok.

---

### Post by Radarguy on 2012-11-19
HI,
I followed your instruction to the T using Ubuntu 12.04 on an Acer Aspire One Netbook.  Everything seemed to go as expected and my Holux M1000 is transferring data to the computer but the xgps does not see anything nor any other GPS program I have.
Any clues anyone?

---

### Post by wildmanne39 on 2012-11-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

