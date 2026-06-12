---
title: "Player 2.0.4 and ttyUSB0 help"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by omairkha on 2007-10-24
Hi all!

Im running Kubuntu Fiesty Faun on a Toshiba Satellite U205-S5034 with 2GB ram.

Im really new to linux (learning the system on the fly here as I go along attempting my project)

Im trying to interface an Evolution ER1 robot to the Player 2.0.4 ER1 plugin driver throught the usb-serial interface provided by ttyUSB0 but having problems.

my player config file (er1.cfg) is as follows:

```

# Basic Player config file for ER1.

driver
(
  name "er1"
  provides ["position2d:0"]
  port "/dev/ttyUSB0"
)

```

when I turn on and plug in the robot to the usb, the system seems to recognize it properly. here is a sample of what comes up in "dmesg" after plugging in the er1:

> 
[ 1469.192000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 1469.372000] usb 4-1: configuration #1 chosen from 1 choice 
[ 1469.376000] ftdi_sio 4-1:1.0: FTDI USB Serial Device converter detected
[ 1469.376000] drivers/usb/serial/ftdi_sio.c: Detected FT8U232AM
[ 1469.376000] usb 4-1: FTDI USB Serial Device converter now attached to ttyUSB0 


The next step is to start player with the er1.cfg file i posted a copy of above:

> 
omair@omair-kbuntu:~/resl/ER1$ player er1.cfg

* Part of the Player/Stage/Gazebo Project [ [http://playerstage.sourceforge.net]](http://playerstage.sourceforge.net]).
* Copyright (C) 2000 - 2006 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig, and contributors. Released under the GNU General Public License.
* Player comes with ABSOLUTELY NO WARRANTY.  This is free software, and you 
* are welcome to redistribute it under certain conditions; see COPYING
* for details.

discovering drivers
Listening on ports: 6665


everything seems to be normal so far.. so i move on to try to start the playerjoy client program (here is where the problems start):

> 
omair@omair-kbuntu:~$ playerjoy -k
Connecting to Player at localhost:6665 - calling connect 
done
playerc error   : timed out waiting for server reply to request 1:0:3:3
playerc error   : failed to get response
terminate called after throwing an instance of 'PlayerCc::PlayerError'
Aborted (core dumped) 


looking back at the player server window, this is the output message:

> 
accepted client 0 on port 6665, fd 5
Evolution Robotics evolution_rcm connection initializing (/dev/ttyUSB0)... 
read() failed: Resource temporarily unavailable
failed to read response
read() failed: Resource temporarily unavailable
failed to read response


from what i can gather, player is working fine but it couldnt communicate with the er1 for some reason. my friend seems to think it might be a problem with my laptop's usb-serial controller. but i have no clue what to do next to try and fix this. 

if anyone has any suggestions they are greatly welcomed! =)

-Omair

---

### Post by ianfp on 2008-05-31
Similar problem here, Omair, using a SICK 200 laser doodad.

---

### Post by orkomedix on 2008-06-26
I know this post is literally ages ago but I wonder if someone has solved the problem ?! I am getting the same messages when trying to connect a LMS 200 with a new ubuntu 7.04 running on a quad core cpu.

I first thought it was a timing problem, but with an older Version (Suse 9.3) everything works finne on the very same machine...


Greetings
orkomedix

---

