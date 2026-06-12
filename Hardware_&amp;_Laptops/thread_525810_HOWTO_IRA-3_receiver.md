---
title: "HOWTO: IRA-3 receiver"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by kfrance on 2007-08-14
I spent some time trying to get my ira-3 receiver from home-electro.com to work so I wanted to post here how I eventually got it to work in feisty fawn.

Let's first check that the device is working.  Type the following into a terminal:
> cat /dev/ttyS1
My device is plugged into the second serial port so you might have to change the number at the end to match the serial port that you have the device plugged into.  If everything went well you will see the red light come on on the device. You could use a remote control at this point and see garbage displayed on the terminal.

This is a irman device.  That is great news because that means that no modules need to be loaded into the kernel.  I went through several tutorials for lirc and spent a lot of time trying to get the right module loaded and come to find out there was no need.  Make sure that you have libirman-dev installed. 
> sudo apt-get install libirman-dev 
I also saw that irman doesn't work with the newer version of lirc that comes installed in feisty so I had to use the older lirc package(version .8.0) that is in the edgy repository.  So I added this line to /etc/apt/sources.list
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
Then I forced synaptic to install the older version.  By installing a older version however update-manager is going to ask you to update to the new version every time. To get rid of this problem add (or create the file if it is not there) to the file /etc/apt/preferences the following:
>  Package: *
Pin: release a=feisty
Pin-Priority: 650

Package: lirc
Pin: version 0.8.0*
Pin-Priority: 1001

There are now three configuration files that I needed to change, /etc/lirc/hardware.conf, /etc/lirc/lircd.conf and ~/.lircrc.  hardware.conf tells lirc what driver and device to use, etc. lircd.conf maps commands from your remote control to english labels that you give it and .lircrc tells the individual programs what to do when a button on the remote control is pressed.
Here is what my hardware.conf file looks like:
> DRIVER="irman"
DEVICE="/dev/ttyS1"
LIRCD_CONF="/etc/lirc/lircd.conf"
MODULES="UNCONFIGURED"
LIRCMD_CONF="UNCONFIGURED"
You might want to change the serial port that is used but that should be all the changes that you need to make i.e. /dev/ttyS1 -> /dev/ttyS0.
If your remote control is listed at [http://lirc.sourceforge.net/remotes]("http://lirc.sourceforge.net/remotes/") than you can just use the lircd.conf file there. The structure of the file is simple and you should be able to look at it and see how it works.  Remember that it is mapping infrared commands to English labels that can be used in the .lircrc file.  If your remote control is not there than you'll need to make one using irrecord. Type
 > irrecord lircd.conf
Then just follow the instructions and in the end you will have a lircd.conf file.
To test if everything worked type
> irw
and then press buttons on the remote control.  You should see the labels that you gave buttons displayed in the terminal when you press the right button.
Next you need to make a .lircrc file.  All the mappings in this file will have a similar structure but will depend on the program you want to use lirc with. With xine you can type 
> xine --keymap=lirc
and it will give you a skeleton file to fill out.  Search the web for other programs you might want to use with lirc.

That is about all the advise I can think up right now.  Let me know if there is something I left out. Good luck!

---

### Post by lank23 on 2007-10-17
Worked well for me using the irman unit that I had laying around, but I had a line in my lirc.conf file that read "toggle_bit_mask 0x0" and this caused LIRC not to show any info on the terminal screen.  So once I removed that line for the file it is working like a charm.

lank23

---

