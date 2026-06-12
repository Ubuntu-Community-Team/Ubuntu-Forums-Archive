---
title: "rc.local not executing on bootup"
date: 2008-07-20
forum: General Help
---

### Post by hluser on 2008-07-20
Hi,

I have had problems getting rc.local to execute during startup. Doe anybody know what file is supposed to call rc.local. Is it supposed to be called from inittab? Also I did a forum search and ran accross some clues but need some help understanding them.

On one thread 'lamego' advised adding the following lines to rc.local to see if it is being executed.

```
echo $(date) - Running >> /var/test.runReboot and check /var/test.run

To check your scripts errors just use:/path/to/script > /var/myscript.log 2>&1
```

I would like to know what the 2>&1 does in the second script test. 

After 'lamego' wrote this, tbeld responded back:

"This is exactly what I needed. Thank you so much. After adding the above to rc.local, I was able to find out what was going on. The JAVA_HOME variable was not defined at boot since it is in ~/.bashrc and so all I needed was to export the path in the script- a stupid mistake but I missed it."

I am not sure about any of this. Can anyone enlighten me on what the JAVA_HOME variable is and where it is located. What is the ~/.bashrc and what needs to be exported in what script?

Thanks

---

### Post by kevdog on 2008-07-20
Can you post your entire rc.local file?

---

### Post by hluser on 2008-07-25
Here is the complete rc.local. I have already chmoded the file 777.

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

echo $(date) - Running >> /var/test.run
#/etc/rc.local > /var/myscript.log 2>&1

# Setup NFS
/etc/init.d/portmap start
/usr/sbin/rpc.mountd
/usr/sbin/rpc.nfsd
/sbin/rpc.statd
/sbin/rpc.lockd
rpcinfo -p
exit 0

```

---

### Post by caljohnsmith on 2008-07-25
First of all, is the rc.local file you refer to located in the /etc directory? Just want to make sure that there's no issue with that. If you want to see if it gets executed, you can put any arbitrary command in it to do something, such as:
```
echo "rc.local executed successfully" > /tmp/rclocal_executed
```
The above command will create a file in /tmp called "rclocal_executed" and it will contain the text "rc.local executed succesfully". So if you put that in your rc.local file, reboot, and if you see that /tmp/rclocal_executed file exists after logging in, then you know rc.local ran just fine. I would stick that command right after the last comment line (# By default this script does nothing) in rc.local so it is the first command executed.

---

### Post by VMC on 2008-07-25
> **hluser said:**
> 
I would like to know what the 2>&1 does in the second script test. 
 
There are three File Descriptors(FD) referred to as **STDIN**, **STDOUT**, and **STDERR** (Numbered as 0,1,2 respectively)
2>&1: means STDERR(2) is redirected to &1. & is the address of STDOUT(1).
So STDERR is redirected to STDOUT.

---

### Post by Vivaldi Gloria on 2008-07-25
> **hluser said:**
> I have had problems getting rc.local to execute during startup.

Check that root owns rc.local and it is executable: -rwxr-xr-x

---

### Post by hluser on 2008-07-28
rc.local is in /etc
an ls -l of rc.local shows
-rwxrwxrwx 1 root root 508 Jul 25 12:20 rc.local

What file runs rc.local?

VMC doesn't the 2>&1 need an & before the 2 and if not why? Btw thanks for the info on how this works.

> Re: rc.local not executing on bootup

--------------------------------------------------------------------------------

Quote:
Originally Posted by hluser  
I would like to know what the 2>&1 does in the second script test.  

There are three File Descriptors(FD) referred to as STDIN, STDOUT, and STDERR (Numbered as 0,1,2 respectively)
2>&1: means STDERR(2) is redirected to &1. & is the address of STDOUT(1).
So STDERR is redirected to STDOUT. 

---

### Post by VMC on 2008-07-28
> **hluser said:**
> rc.local is in /etc
an ls -l of rc.local shows
-rwxrwxrwx 1 root root 508 Jul 25 12:20 rc.local

What file runs rc.local?

VMC doesn't the 2>&1 need an & before the 2 and if not why? Btw thanks for the info on how this works.

The "&" before the 2 means to put command in background. Try this

'ls 2>&1' , then this ls &2>&1' and you will see a background started.

---

### Post by Vivaldi Gloria on 2008-07-29
> **hluser said:**
> What file runs rc.local?

rc.local is called by s99rc.local files in the /etc/rc2.d - /etc/rc5.d folders.

The files in the /etc/rc2.d - /etc/rc5.d folders are called by rc2 - rc5 files in the /etc/event.d folder.

And it's the /sbin/init process which is responsible of starting or stopping the events in /etc/event.d folder.

---

### Post by Vivaldi Gloria on 2008-07-29
Actually, why don't you look at your boot messages. See if you get

```
Running local boot scripts (/etc/rc.local)
```

Also, did you try caljohnsmith's advice above?

How about you change rc.local to a simple one like

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

echo "rclocal executed successfully" > /home/<your_username>/rclocal_executed 
exit 0
```

With this rc.local do you get a rclocal_executed file in your home folder when you boot up?

---

### Post by hluser on 2008-07-29
Ok.

I treid caljohnsmith's suggestion and rc.local is still not executing. I simplified it as you suggested but still it is not being executed. It is chmoded 755. I also tried dmesg | grep 'Running local boot scripts (/etc/rc.local)' but this did not show anything. The /var/log/messages also showed nothing in it regarding rc.local.

---

### Post by Vivaldi Gloria on 2008-07-29
> **hluser said:**
> Ok.

I treid caljohnsmith's suggestion and rc.local is still not executing. I simplified it as you suggested but still it is not being executed. It is chmoded 755. I also tried dmesg | grep 'Running local boot scripts (/etc/rc.local)' but this did not show anything. The /var/log/messages also showed nothing in it regarding rc.local.

The boot messages are not logged in /var. dmesg doesn't show them either. There was a thread around about enabling the logging of boot messages. Search for that thread if you want.

I suggest you simply read the messages during boot. See erginemr's posts here:

[http://ubuntuforums.org/showthread.php?t=696538](http://ubuntuforums.org/showthread.php?t=696538)

If it scrolls really fast then you may have to disable starting X (gnome) by default. See for example
[http://ubuntuforums.org/showthread.php?t=682151](http://ubuntuforums.org/showthread.php?t=682151)

---

### Post by hluser on 2008-08-02
I tried enabling the logging of boot log messages by changing 

/etc/default/bootlogd:

# vi /etc/default/bootlogd

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

This did not yield anything in the var/log/boot files. I also fount that if I run etc/init.d/rc.local with sh /etc/init.d/rc.local start it will run etc/rc.local. I do not know what file calls etc/init.d/rc.local. Does anyone know what files calls it?

---

### Post by Vivaldi Gloria on 2008-08-02
> **hluser said:**
> I also fount that if I run etc/init.d/rc.local with sh /etc/init.d/rc.local start it will run etc/rc.local. I do not know what file calls etc/init.d/rc.local. Does anyone know what files calls it?

/etc/rc2.d/s99rc.local is linked to /etc/init.d/rc.local and the files in the /etc/rc2.d folder are started by the rc2 file in the /etc/event.d folder during boot.

---

### Post by hluser on 2008-08-03
The S99rc.local symbolic link was missing so I recreated it in the /etc/rc2.d folder. I set it up the same way the rest of the symbolic links in the rc2.d folder are setup. After rebooting rc.local still does not execute. I am not sure why. I checked SS89cron, which is in the same folder, to see if it was executing on boot and it is working. So now I am very confused.

---

### Post by Vivaldi Gloria on 2008-08-03
> **hluser said:**
> The S99rc.local symbolic link was missing so I recreated it in the /etc/rc2.d folder. I set it up the same way the rest of the symbolic links in the rc2.d folder are setup. After rebooting rc.local still does not execute. I am not sure why. I checked SS89cron, which is in the same folder, to see if it was executing on boot and it is working. So now I am very confused.

Try commands of the sort

```
sudo update-rc.d rc.local defaults 
sudo update-rc.d rc.local multiuser 
sudo update-rc.d rc.local start <some_numbers>

```

See

```
man update-rc.d 
```

for more info. First use with the flag

```
-n     Don’t do anything, just show what we would do.
```

---

### Post by hluser on 2008-08-04
Ok.

I tried to run update-rc.d but it said the symbolic link existed so I deleted the link I had created manually. After that I ran update-rc.d and it created a set of new links for all the run levels. I rebooted and rc.local ran like it is supposed to! That fixed the problem. Thank you! :KS



On a side note I am wondering why the manually created sym link I created did not work. Do you know why?

---

### Post by Vivaldi Gloria on 2008-08-04
> **hluser said:**
> Thank you! 

You're welcome.

> **hluser said:**
>  On a side note I am wondering why the manually created sym link I created did not work. Do you know why?

I have no idea.

---

