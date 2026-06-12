---
title: "trouble getting udev rules.d to run my script"
date: 2008-12-14
forum: Hardware
---

### Post by tastygroove on 2008-12-14
hello

i'm trying to convert an old laptop to a digital picture frame and i'm running in to a little snag.  

the laptop boots straight in to gnome and the photo slideshow program (i'm using a program called feh) is automatically run.  i want to be able to upload photos automatically using a usb drive.  i've created a udev rule that mounts the usb drive and runs a script.  the script kills feh, copies any .jpg files from the usb drive on to the laptop, then restarts feh.  

here is the udev rules.d file

```

KERNEL=="sd*", BUS=="usb", TYPE=="disk", ACTION=="add", RUN+="/bin/mkdir /media/usbdrive"

KERNEL=="sd*", BUS=="usb", TYPE=="disk", ACTION=="add", RUN+="/bin/mount -t auto /dev/%k /media/usbdrive"

KERNEL=="sd*", BUS=="usb", TYPE=="disk", ACTION=="add", RUN+="/usr/local/bin/copypics.sh"

```

here is the script 'copypics.sh'

```

#!/bin/bash

killall feh

cp /media/usbdrive/*.jpg /home/user/pics/

su user -c feh -zZFr -D 300 /home/user/pics/

```


everything works fine except feh does not get restarted.  i've tried running the script copypics.sh from the command line (as root) and it works just fine.  but for some reason when it is executed by my udev rule it does not.  i'm not even sure how view any errors that it is producing.  

i have a feeling that the problem lies with trying to start an x application from udev.  maybe its a permissions issue?  or maybe there is a more elegant way to do the same thing?

any ideas?

thanks!

---

### Post by sarang on 2008-12-14
I have a few suggestions/hints:

1. Have you played with the udev rules priorities? In particular, have you tried a priority between 90 and 95? Yes, I know it is not the standard priority value for custom scripts.

2. Perhaps the X server is rejecting connections because of the absence of the magic cookie (I you do not know what I am talking about, please reply saying so and I will elaborate). To correct this, have you tried adding a line to your script that is something like:

```
export XAUTHORITY=/home/username/.Xauthority
export DISPLAY=:0.0
```, where 'username' is the username that you usually login as? If that works, it could be a quick hack, but it will not work if the user logged in at the desktop is not you. To make it work for all users, you could edit the script to find valid .Xauthority files (which should be fairly easy) and then automatically infer the username and export the appropriate path.


I also suspect that there could be some complications because of udev passing control to hal which does not return control back...

Anyway, another thing that could be useful: I have a working script that runs a backup command when a specific external drive is connected. I think you could edit the name of the program to be launched to feh and add the export .Xauthority lines and it is highly likely that it will work. This script is posted at:

[http://ubuntuforums.org/showthread.php?t=984671](http://ubuntuforums.org/showthread.php?t=984671)

3. If the Xauthority hack does not work at all, you might have a stale .Xauthority file. To check this, launch a terminal after logging in through the gui login (i.e when you have a graphical desktop) and run:
```
echo $XAUTHORITY
```
You should see something like
```
/home/username/.Xauthority
``` 
as the output. If instead you see something like
```
/tmp/something
```
then you have a stale Xauthority file. To correct this, boot your comuter into the rescue mode or stop gdm, and delete the stale file by running
```
rm -f /home/username/.Xauthority
```
Then reboot into regular graphics mode (runlevel 2)and check again if 
```
echo $XAUTHORITY
```
gives the right output.

4. If `echo XAUTHORITY' does indeed give the correct output, then try adding debug statements like 


```
echo "Script launched" >> /tmp/temp-feh-script-log
```
and see if the file /tmp/temp-feh-script-log is created. If it is not, your script is not being launched at all and you probably need to play with the rule priorities.

5. Also consider the 

```
sudo udevadm monitor
```
command.

6. Finally, if your script is being run but something else is the problem, to debug the hard brute-force way, add the statement 

```
echo `env` >> /tmp/temp-feh-script-log
```
to the script and check the /tmp/temp-feh-script-log file. Note that the quotes surrounding the word env in the above command are backticks - the ones on the ~ key on a qwerty keyboard.

Then run the env command in a shell where your script does work. Then manually compare the two environments and find out exactly which environment variables are necessary for your script. IMO the best way to do this is by running 
```
unset variablename
``` 
in the shell where your script works, where variablename takes each of the variable names you see in the output of env. However do not run 'unset path'. To be more clear, the output of env will be of form variable1=value1 variable2=value2.....

I am suggesting running unset variable1 then unset variable2 and so on but never running unset path and finding out the minimal set of environment variables required to make you script run successfully. Then export those explicitly through your script and then it should run even when launched by udev.

7. Change permissions of the mountpoint /media/usbdrive to 777 in the script while trying to debug to make sure you never encounter a permissions issue.

One more thing: I suggest that you do not mount the drive through your script if you can do without it. See the backup script thread link I posted above for a IMO better way of doing this. The reason I say this is because random gui applications relying on the hal automounter can break if you bypass it... Also, you make the directory /media/usbdrive but never delete it which is less than ideal as from a programming point of view, your program should have the least number of side effects.

---

### Post by tastygroove on 2008-12-15
first of all i want to say thank you so much.  your post was very helpful and informative.  

it turns out that checking the environment variables did the trick.  i su'd to root, then tried running my copypics script over and over, unsetting one env variable at a time.  (comparison of the env variables for the udev environment and regular user environment exposed the fact that the two sets were nearly mutually exclusive) when i unset HOME, feh spit out an error that said something about it being helpful if i set the HOME variable.  so i manually set HOME in the copypics script, plugged in my USB drive and voila!  it worked.

as for the manual mounting of the usb drive, i initially tried allowing the system to automount but it wasn't working.  what was happening (and here i should mention that i'm running xubuntu) is i would plug in the device, an icon would appear on the desktop, but the system was not mounting the drive.  if i went to the /media/ directory, no usb device was listed.  the system would mount the drive only after accessing it via the desktop icon.

anyway, i'll have a look at your script to see how you handle mounting.  now that i've got this all working i would like to make it work elegantly.  i'll be trying to optimize from this point forward (yes, including removing the /media/usbdrive directory, thanks for the tip :-)

thanks again!

---

### Post by sarang on 2008-12-16
Glad it works now...

BTW, I did gather from what you were trying to do that you were not new to linux, but still decided to write for a newbie so that if one reads it in the future, hopefully s/he will not be hopelessly confused. Sorry if I sounded condescending.

---

### Post by actmnophn on 2009-01-04
> **sarang said:**
> Glad it works now...

BTW, I did gather from what you were trying to do that you were not new to linux, but still decided to write for a newbie so that if one reads it in the future, hopefully s/he will not be hopelessly confused. Sorry if I sounded condescending.

Thank you. I am that newbie and do appreciate it. I do not really understand yet all you wrote but I have enough to research and figure out. I am trying the same thing to make a udev rule to run a script when I insert a specific drive.
I was also trying to run feh, I had a question about it so I might as well post it here, even though I am not up to this problem yet.

It is suggested that any program thatis run using run in a udev rule should not last too long bec the rest of udev is waiting till it finishes. If it is run from a script is that considered detatched from udev?

thanks again.:KS

---

