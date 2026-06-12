---
title: "terminal command on bootup"
date: 2008-09-16
forum: General Help
---

### Post by LightningEagle on 2008-09-16
I've got this old computer at home running a local apacheserver which my father uses for backup and I use it to run my php-script.

My problem is that we don't have a screen for the pc which makes it rather troublesome to run the server without being able to see what happen.

Is it possible to have ubuntu run the terminal command, to start the server, automatically on bootup? 

It might be important to add that it asks for password in order to run the command with the right privileges. Can i bypass that too?

Hope I made myself clear... :)

---

### Post by qstraza on 2008-09-16
well if you use apt-get to install apache, than the script should be in /etc/init.d and should be runned automaticly at boot time.

Well root runs apache, accully www-data does. So put your line which starts the apache in a bash file and chmod +x it and move it to the /etc/init.d/

---

### Post by LightningEagle on 2008-09-16
Maybe I should add that the apacheserver is the one called xampp from apachefriends.org because that's the one I know how to handle. 

Would you recommend using the one you suggested instead of the xampp?

---

### Post by qstraza on 2008-09-16
tell me how do you start your apache

---

### Post by LightningEagle on 2008-09-16
I open the terminal

write: \opt\lampp\lampp start
then it asks for root password. ***********
and it runs. 

\opt\lampp\lampp stop <-- this is the command for stopping the server.

It is explained here too: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by unutbu on 2008-09-16
Here is one way to make a script or program run at startup as root:
Edit /etc/rc.local
```

gksu gedit /etc/rc.local
```

Add the script/program command above the "exit 0" line

---

### Post by qstraza on 2008-09-16
> **LightningEagle said:**
> I open the terminal

write: \opt\lampp\lampp start
then it asks for root password. ***********
and it runs. 

\opt\lampp\lampp stop <-- this is the command for stopping the server.

It is explained here too: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
So add that line in the /etc/rc.local, so system will run it at boot time and there is no need for password.

Btw, why backslashes?

---

### Post by LightningEagle on 2008-09-16
> **qstraza said:**
> Btw, why backslashes?

I honestly don't know... :confused:

Thanks for your help unutbu and qstraza. I'll try the rc.local solution. Sure hope it works. :)

---

### Post by qstraza on 2008-09-16
it will work, just try the command before you put it in the rc.local, so you dont make any mistakes ;)

---

### Post by LightningEagle on 2008-09-21
How about a file for commands to run when closing the computer?
Does that exist too?

---

### Post by unutbu on 2008-09-21
```
gksu gedit /etc/init.d/myscript

```
```
#!/bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
. /lib/lsb/init-functions

case "$1" in
    start)
	echo -n "Starting myscript"
	/opt/lampp/lampp start
        ;;
    restart|reload|force-reload)
	echo -n "Restarting myscript"
	/opt/lampp/lampp stop
	/opt/lampp/lampp start
        ;;
    stop)
	echo -n "Stopping myscript"
	/opt/lampp/lampp stop
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```
Change the "/opt/lampp/lampp" commands above if necessary.
Save myscript.
While still in gedit, open /etc/rc.local
Remove the lines you put there to start lampp. We will now do it a different way.
Save the edited /etc/rc.local
```

sudo update-rc.d myscript defaults 99

```
This will make "myscript start" run when you boot up, and 
"myscript stop" run when you shutdown. 

"myscript start" runs "/opt/lampp/lampp start" and
"myscript stop" runs "/opt/lampp/lampp stop"

---

### Post by LightningEagle on 2008-09-28
At last I got to try this script on the computer but it doesn't really seem to work... :/

At least I can see that the server isn't starting up and I guess that means it doesn't shut down either. 

Any idea why it doesn't work for me?

---

### Post by unutbu on 2008-09-28
Let's first test if the script works from the command line: Does LAMP start when you type

```
sudo /etc/init.d/myscript start
```

If that doesn't work, check that the script is executable:
```

sudo chmod +x /etc/init.d/myscript
```

Then try the "sudo /etc/init.d/myscript start" command again. 

If it still does not work type
```

ls -l /etc/init.d/myscript
ls -l /etc/rc2.d | grep myscript
ls -l /opt/lampp/lampp

```

and post the output of all the commands above.

---

### Post by LightningEagle on 2008-09-28
> **unutbu said:**
> Let's first test if the script works from the command line: Does LAMP start when you type

```
sudo /etc/init.d/myscript start
```
Didn't work!

> **unutbu said:**
> 
If that doesn't work, check that the script is executable:
```

sudo chmod +x /etc/init.d/myscript
```

Then try the "sudo /etc/init.d/myscript start" command again. 
Did work! :D Now it works when I boot up too... Thanks! 

Are there any way to check if the terminate command command is successfully executed when i shut down the computer?

---

### Post by unutbu on 2008-09-28
Great. First check that the stop command works from the terminal:```


sudo /etc/init.d/myscript stop

```
Then check that LAMP is not running. (use "ps axuw", System>Administration>System Monitor, or access a web page that requires LAMP.)

Then, to make sure that the script is being run when you shut down, you can do something like this:
```

gksu gedit /etc/init.d/myscript
```

Add an echo line like this:

Change
```

    stop)
	echo -n "Stopping myscript"
	/opt/lampp/lampp stop
        ;;

```
to
```

    stop)
	echo -n "Stopping myscript"
	echo "Stopping myscript" > /root/myscript.out
	/opt/lampp/lampp stop
        ;;

```

Next time you reboot, run this:
```

ls -l /root/myscript.out

```
You'll see something like this:
```

-rw-r--r-- 1 root root 53 **2008-09-28 13:35** /home/root/myscript.out
```

The presence of this file is a good indicator that "/opt/lampp/lampp stop" was run.

---

### Post by LightningEagle on 2008-09-28
It works flawlessly (I hope :D)!

You are simply awesome! 
Thank you so many times for all the help! :D

---

