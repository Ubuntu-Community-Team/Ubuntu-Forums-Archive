---
title: "howto run a .sh file at boot"
date: 2005-11-15
forum: General Help
---

### Post by sbaush on 2005-11-15
Hi, I have to run this .sh file everytime i use ubuntu
```
sudo sh /usr/local/bin/html2pop3/html2pop3.sh start

```
This allow me to use my mail account with every internet provider. 
How can i launch this at boot time?
Thanks to all...

---

### Post by cedjo on 2005-11-15
create this file in your favorite editor (sudo gedit)

```

#!/bin/sh
# run html2pop3 at boot

case "$1" in
'start')
	/usr/local/bin/html2pop3/html2pop3.sh start
	;;
'stop')
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0

```

save it as /etc/init.d/html2pop3 (you must be root)

to test your script type /etc/init/html2pop3 start
That's it!

each time you'll reboot this script will launch html2pop3.sh

---

### Post by Sheco on 2005-11-15
uhm, creating /etc/init.d/html2pop3 will not start it at runtime, you'll have to create a symlink at /etc/rc2.d

```
cd /etc/rc2.d
ln -s ../init.d/html2pop3 S70html2pop3
```

Here I used S70 but you can move it around to make it start sooner or later than other processes. (most are around S20)

---

### Post by sbaush on 2005-11-15
i tried both your solutions but doesn't run...
i have to type in terminal ```
sudo sh /usr/local/bin/html2pop3/html2pop3.sh start
``` to run html2pop3.
New ideas??
Thanks a lot!!!

---

### Post by Sheco on 2005-11-15
you have to follow cedjo's instructions then mine

try this to make the script executable and reboot:
```
chmod +x /etc/init.d/html2pop3
```

---

### Post by sbaush on 2005-11-15
:KS :KS WOW!!! :KS :KS 
Now it's OK!!!
Thanks!!!

---

### Post by lizardking on 2005-11-15
[QUOTE=sbaush]:KS :KS WOW!!! :KS :KS 
Now it's OK!!!
Thanks!!![/QUOTE]
power of ubuntu guru..:cool:

---

### Post by cedjo on 2005-11-16
[QUOTE=Sheco]you have to follow cedjo's instructions then mine

try this to make the script executable and reboot:
```
chmod +x /etc/init.d/html2pop3
```[/QUOTE]

Yes my fault.... I forgot to tell that the script must be executable....
Sorry!

---

### Post by eneve on 2008-04-08
Hi, I have done everything that this thread asks for and I still am not getting the script to run at startup. In particular, I am trying to get a Jetty server (running Apache Archiva) to fire up when linux starts.  I will be wanted this functionality with Apache Continuum next...

I have a file /etc/init.d/archiva that looks as follows:

```

#!/bin/sh
# run archiva at boot

case "$1" in
'start')
	/var/lib/apache-archiva-1.0.1/bin/linux-x86-32/run.sh start
	;;
'stop')
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0

```

Then I made that file executable:

```

chmod +x /etc/init.d/archiva

```

Then I created the symlink:

```

cd /etc/rc2.d
ln -s ../init.d/archiva S70archiva

```

After all this the server is not running, and I have to start it manually when I enter my session.

```

sudo /etc/init.d/archiva start

```

I am thinking that it has something to do with Java???  Any help would be much appreciated!

---

### Post by Slim Odds on 2008-04-08
rc.local is generally the place to put custom startup stuff.

---

### Post by chilinski on 2008-04-08
You could also put it in your profile so it runs only when you log on (in case multiple users are on your computer). It goes in either .bash_profile, .profile or similar.

---

### Post by eneve on 2008-04-09
So I edited my /etc/rc.local file to look like this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/apache-archiva-1.0.1/bin/linux-x86-32/run.sh start
exit 0

```

And the server was not started when I logged into the box.

However I went to the command line and ran:

```

user@my-desktop:~$ sudo /etc/rc.local 
[sudo] password for user:
Starting Archiva...

```

And then the server started up without error.

I did try sticking it in my /etc/bash.bashrc file where I have all of my development environment variables, but that did not work either.

---

