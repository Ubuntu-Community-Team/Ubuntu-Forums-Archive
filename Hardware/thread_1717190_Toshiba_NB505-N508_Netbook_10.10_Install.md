---
title: "Toshiba NB505-N508 Netbook 10.10 Install"
date: 2011-03-29
forum: Hardware
---

### Post by dehager on 2011-03-29
This is my first post to the forum so I thought I would try to be constructive and helpful to all...

 
The goal was to have a Netbook running Ubuntu so I could access internet, e-mail and video chat while traveling. I also needed to use Google Earth and transfer GPS waypoints with my Garmin 60CSx. I decided to purchase a Toshiba NB505-N508 with 2G of memory after researching Netbooks. The only issues I found while researching was loss of battery power while shut down on early NB505 Netbooks and Wi-Fi drivers not installed, nothing of any major importance with the newer NB505-N508 Netbooks. Before wiping the Windows 7 Starter from the drive I ran Belarc Advisor under Windows and printed out the hardware information. The Wi-Fi was listed as a Realtek RTL8188CE Wireless LAN 802.11n.
 
USB Flash Drives were created using the Universal USB Installer and the drive was wiped with DBAN &#8220;Darick&#8217;s Boot and Nuke&#8221;. After connecting the Netbook to the internet using the Ethernet port Ubuntu 10.10 Netbook was installed using the USB flash drive and updates were installed. At this point I did not have Wi-Fi working and installed the Realtek driver update as listed below, once installed the wireless appeared and worked without issue. No issues were found with discharging batteries while turned off.
 
Google Earth 6, Google Talk and Skype installed and worked without issues. I was disappointed that Google Earth 6 did not have GPS support but I can use GPSBabbel to save my waypoints and import the .gpx file into Google Earth. I was not able to get Empathy working with video using my Gmail account but I am confident that the community will eventually get the bugs worked out.
 
With a little up front research all went well and I am now the proud owner of a fully functioning Netbook running Ubuntu 10.10. I am grateful to all who contribute their time and expertise supporting the Ubuntu community. I have no complaints with the Toshiba NB505-N508 running Netbook 10.10 and the minor issues encountered were easy to overcome. I am sure that future updates and bug fixes will add to the functionally of the software. 
 
I am sure that there are many ways to install and configure Ubuntu. This is how I, with very little experience using Ubuntu configured my Netbook&#8230; Again, thanks to all!
 
**_Installing the Realtek Wi-Fi drivers:_**
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
**_Installing Google Talk:_**
Downloaded the application through my Gmail account by clicking on the &#8220;Install voice and video chat&#8221; link and installed with Ubuntu Software Center. Using Gmail in Firefox I was able to connect to a Windows XP work station using Gmail video chat with no issues.
 
**_Installing Skype:_**
Click, click with Ubuntu Software Center. I was able to connect to Skype users with no issues.
 
**_Installing Google Earth:_**
sudo apt-get install lsb-core (lsb-core package must be installed)
sudo apt-get install gdebi-core (this is how I chose to install the .deb package)
 
sudo apt-get install googleearth-package
sudo make-googleearth-package --force
sudo gdebi <*package name*>.deb

---

### Post by mörgæs on 2011-03-29
Thanks for a good guide. I guess that the post feels more at home under 'Hardware & Laptops', so I will ask a moderator to move it. Hoping it is all right with you.
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)


The 'Laptop compatibility list' is a good place for a very brief review, by the way:
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)


Marking the thread 'solved' in 'thread tools' will help you reach people who are looking for an answer.


- and welcome to the fora :-)

---

### Post by dehager on 2011-03-29
mörgæs,

Thanks for the reply. Please move the post if there is a more suitable place for it. I will add a post to the 'Laptop compatibility list'. Looking forward to contributing to the community as I learn more.

Regards,
Dana

---

### Post by ackey on 2011-04-11
Thank you for the excellent post!  It was clear and easy to follow when setting up the netbook.  With 2GB of RAM, I've been very happy with this netbook running UNR 10.10

I've found issues with the Fn-Fkey abilities.  This includes important features like screen brightness and num-lock.  I've managed to get num-lock on, but couldn't turn it off.

The only way I've found to control screen brightness is to use the gconf parameter of dimming on battery.  I wrote a simple shell-script (not very robust) that would allow me to set up keybindings to control the brightness.  The script expects a single parameter, either the word up or down or an integer value to set the brightness to.  While the gconf parameter is actually %dim, I've set this up to be %bright. 

```

nb505 > ./bright.sh up
nb505 > ./bright.sh down
nb505 > ./bright.sh 80

```

```

#!/bin/bash

key_val=$(gconftool -g /apps/gnome-power-manager/backlight/brightness_dim_battery)
let "key_val=100-$key_val"

newval=$1

if [ "X$1" = "Xdown" ]
then
    if [[ $key_val -eq 0 ]] ; then
        echo "Min brightness is set: $key_val"
        exit
    else
        let "newval=$key_val-10"
        echo "Decreased brightness from $key_val to $newval"
   fi     
elif [ "X$1" = "Xup" ]
then
    if [[ $key_val -eq 100 ]] ; then
        echo "Max brightness is set: $key_val"
        exit
    else
        let "newval=$key_val+10"
        echo "Increased brightness from $key_val to $newval"
   fi     
fi

let "newval=100-$newval"

gconftool -s /apps/gnome-power-manager/backlight/brightness_dim_battery -t int $newval


```

---

### Post by jmac0101 on 2011-07-22
> **ackey said:**
> Thank you for the excellent post!  It was clear and easy to follow when setting up the netbook.  With 2GB of RAM, I've been very happy with this netbook running UNR 10.10

I've found issues with the Fn-Fkey abilities.  This includes important features like screen brightness and num-lock.  I've managed to get num-lock on, but couldn't turn it off.

The only way I've found to control screen brightness is to use the gconf parameter of dimming on battery.  I wrote a simple shell-script (not very robust) that would allow me to set up keybindings to control the brightness.  The script expects a single parameter, either the word up or down or an integer value to set the brightness to.  While the gconf parameter is actually %dim, I've set this up to be %bright. 




I am pretty experienced as a general ubuntu user, but shell scripts are a bit beyond me, could you please walk me through the implementation of your script; the dimness of my screen is really starting to bother me. Thank you.

---

### Post by ackey on 2011-08-02
Hi jmac,

Sorry that my initial post wasn't detailed enough.  I'll try to go step by step here... let me know if I have missed anything or misunderstood your question.

1) Save the script (as in the above post) as bright.sh - it can be in your home folder or where-ever.  
2) You will need to make it executable.  You can do this on a terminal
```

computer:~$ chmod u+x bright.sh

```
3) Now on the terminal, in the folder the file is in, you should be able to type
```

computer:~$ ./bright.sh up

```
to make the screen brightness increase.

To make sure it is working try
```

computer:~$ ./bright.sh 0
computer:~$ ./bright.sh 100

```
This should go to minimum brightness and then to maximum brightness.

Once it is working you can bind it to a keyboard shortcut so you don't need to use the terminal.

Where the "keyboard shortcuts" menu is depends on what distribution you are using.  There should be a button called "add".  This should open a dialog for adding a custom shortcut.  You can name it whatever you would like.  Then you put the script with the command. For instance, I have a "DecreaseBrightness" keyboard shortcut with the command of "/home/user/bright.sh down" (no quotation marks in the dialog).  You want to make sure this points to the location/name you have put the script.  Then I also have one that is IncreaseBrightness with a command of "/home/user/bright.sh up".  You could alias it to a specific brightness as well, like two commands that are "/home/user/bright.sh 0" and "/home/user/bright.sh 100".

---

### Post by jmac0101 on 2011-09-01
> **ackey said:**
> Hi jmac,

Sorry that my initial post wasn't detailed enough.  I'll try to go step by step here... let me know if I have missed anything or misunderstood your question.

1) Save the script (as in the above post) as bright.sh - it can be in your home folder or where-ever.  
2) You will need to make it executable.  You can do this on a terminal
```

computer:~$ chmod u+x bright.sh

```
3) Now on the terminal, in the folder the file is in, you should be able to type
```

computer:~$ ./bright.sh up

```
to make the screen brightness increase.

To make sure it is working try
```

computer:~$ ./bright.sh 0
computer:~$ ./bright.sh 100

```
This should go to minimum brightness and then to maximum brightness.

Once it is working you can bind it to a keyboard shortcut so you don't need to use the terminal.

Where the "keyboard shortcuts" menu is depends on what distribution you are using.  There should be a button called "add".  This should open a dialog for adding a custom shortcut.  You can name it whatever you would like.  Then you put the script with the command. For instance, I have a "DecreaseBrightness" keyboard shortcut with the command of "/home/user/bright.sh down" (no quotation marks in the dialog).  You want to make sure this points to the location/name you have put the script.  Then I also have one that is IncreaseBrightness with a command of "/home/user/bright.sh up".  You could alias it to a specific brightness as well, like two commands that are "/home/user/bright.sh 0" and "/home/user/bright.sh 100".
For some reason this did not work for me.
I get the confirmation messages in the treminal telling me I am turning up the brightness:

Increased brightness from 90 to 100

But it makes on change on the screen. I also tried running command as su.

Thanks anyways

---

### Post by jmac0101 on 2011-09-01
> **ackey said:**
> Hi jmac,

Sorry that my initial post wasn't detailed enough.  I'll try to go step by step here... let me know if I have missed anything or misunderstood your question.

1) Save the script (as in the above post) as bright.sh - it can be in your home folder or where-ever.  
2) You will need to make it executable.  You can do this on a terminal
```

computer:~$ chmod u+x bright.sh

```
3) Now on the terminal, in the folder the file is in, you should be able to type
```

computer:~$ ./bright.sh up

```
to make the screen brightness increase.

To make sure it is working try
```

computer:~$ ./bright.sh 0
computer:~$ ./bright.sh 100

```
This should go to minimum brightness and then to maximum brightness.

Once it is working you can bind it to a keyboard shortcut so you don't need to use the terminal.

Where the "keyboard shortcuts" menu is depends on what distribution you are using.  There should be a button called "add".  This should open a dialog for adding a custom shortcut.  You can name it whatever you would like.  Then you put the script with the command. For instance, I have a "DecreaseBrightness" keyboard shortcut with the command of "/home/user/bright.sh down" (no quotation marks in the dialog).  You want to make sure this points to the location/name you have put the script.  Then I also have one that is IncreaseBrightness with a command of "/home/user/bright.sh up".  You could alias it to a specific brightness as well, like two commands that are "/home/user/bright.sh 0" and "/home/user/bright.sh 100".
For some reason this did not work for me.
I get the confirmation messages in the treminal telling me I am turning up the brightness:

Increased brightness from 90 to 100

But it makes on change on the screen. I also tried running command as su.

Thanks anyways

---

