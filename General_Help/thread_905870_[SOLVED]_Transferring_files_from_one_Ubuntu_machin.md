---
title: "[SOLVED] Transferring files from one Ubuntu machine to another?"
date: 2008-08-30
forum: General Help
---

### Post by bobleny on 2008-08-30
I know you can transfer files from one machine to the next, but I don't know how. I've looked for guides and even followed a couple. Setting up samba and nfs and hosting files..... When I was done, I didn't even know how to actually take files from one machine to the other.

I require to way communication between my laptop and my desktop.

Could someone point me to a good guide?

Can't I use apache to do this, or is that asking for trouble? I already have an apache server on both machines....


Thank you for all of your help!

---

### Post by retrovertigo on 2008-08-30
If they both have a network connection, then you can install the ssh package on both computers, and then use **scp** to do the copying.  Here's some example syntax:

```
scp -r oldcomputer_folder username@newcomputer:~
```

The above will recursively copy a folder called "oldcomputer_folder" from the old computer to the home directory of username's folder on the new computer.  "newcomputer" can be either a hostname or IP address.

If you've got a lot to move though, it might just be easier (if you've got some spare space on the old computer's hard drive) to put it all into a tar archive and compress it, then transfer the archive to the new computer and unpack it there.

Another way that I've transferred files in the past is with a USB flash drive, you may want to consider that if you have one handy.

---

### Post by bobleny on 2008-08-30
Thanks for the quick reply!

Flash drive is what I have been useing but the speed is horrible and I can only trasnger about 2GBs at a time... I've got about 12GBs of data to move...

My only problem with you suggestion is that I don't know how to give my computers an IP or host name....

I don't suppose you know how to set an IP address or host name up?

---

### Post by retrovertigo on 2008-08-30
> **bobleny said:**
> Thanks for the quick reply!

Flash drive is what I have been useing but the speed is horrible and I can only trasnger about 2GBs at a time... I've got about 12GBs of data to move...

My only problem with you suggestion is that I don't know how to give my computers an IP or host name....

I don't suppose you know how to set an IP address or host name up?

If you've got a network connection then your computers should already both have an IP address.  Are they both behind a router?  Run ifconfig from a terminal to see the IP.  The IP address for each interface will show up on a line that begins with "inet addr:".  Usually the default interface is **eth0** if you're connected with an ethernet cable, and **wlan0** if you're connected wirelessly.  Here's an example of the output:

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:cf:12:fc  
          inet addr:192.168.3.139  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fecf:12fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1287969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1263288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:620182588 (591.4 MB)  TX bytes:1018681559 (971.4 MB)
```

---

### Post by bobleny on 2008-08-30
I tried that...

```
bob@GeorgeJr:~$ scp -r "/home/bob/07 -Hail Caesar.mp3" bob@192.168.3.102:~
ssh: connect to host 192.168.3.102 port 22: Connection refused
lost connection
```

Any ideas as to what I did wrong?

And yes, both computers are running through a router...

---

### Post by retrovertigo on 2008-08-30
Make sure you have the ssh package installed, on *both* computers.

```
sudo apt-get install ssh
```


Also, in case you didn't know already, "~" is shorthand for the user's home directory, so it'll copy that file to /home/bob on the new computer.  You can use "~/Music" instead of "~" if you want to copy it directly to the Music folder on the new computer.  Likewise, you don't need to enter the full path to the files on your old computer.  Since you're already in your home directory, you can use the following:

```
scp -r "07 -Hail Caesar.mp3" bob@192.168.3.102:~
```

---

### Post by retrovertigo on 2008-08-30
Oh, and one more thing about scp... you can also copy the data from your old computer to the new computer, while logged into the new computer.  Just use something like this:

```
scp -r bob@192.168.3.101:"~/07 -Hail Caesar.mp3" .
```

Note: this assumes that the old computer's IP is 192.168.3.101, and that you are running this command from the new computer.

---

### Post by bobleny on 2008-09-01
I typed: ssh in the terminal on both computers and got the same message on both.

```

bob@GeorgeJr:~$ ssh
usage: ssh [-1246AaCfgKkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w local_tun[:remote_tun]] [user@]hostname [command]

```

So, wouldn't that mean the both have ssh installed on them?

----------

I also tried transferring files from the desktop to the laptop and vice versa. In both cases I receive the same message:
```

ssh: connect to host 192.168.X.XXX port 22: Connection refused
lost connection

```

---

### Post by chronos00 on 2008-09-01
After installing the SSH package I think you need to restart Ubuntu (in order to the SSH server to activate).

After that, if you have both of your PCs conected to a common router (via ethernet cable or wireless) just type in each PC: "ifconfig" and look for your "inet addr" (wich in fact is your IP address).

The EASIEST way to transfer files at this point is: in Ubuntu's Desktop, click on "Places" (just beside "Applications") and then on "Connect to server"
Set "Service type" to -> "SSH"
"server" -> "the ip address of the PC you want to connect" (in this case, the OTHER PCs IP)
"port" -> "22"
"folder" -> "/"
"username" -> "the user name wich you use to log in at the remote computer"

After this, you just need to supply the password and this will open a just regular "explorer-like" window with all the files on the remote PC.

Al of this will be possible if your PCs have correctly set IP addresses (done automatically by a regular wifi-router)
If you need to manualy set IP addresses You will have to tell us the specific configuration of your network so that be can help you.

Hope this helps!

---

### Post by bobleny on 2008-09-01
Thanks, chronos00. Does that program, "Connect to Server" have an application name? Chances are, being that I am on Kubuntu, I will need to run the program based on it's name or install it.

Thanks for the help though. I just need to know the program name.

---

### Post by joenix on 2008-09-01
The output you got from typing 'ssh' in the terminal only indicates that the client package is installed (openssh-client). The server is provided by a different package (openssh-server). Please make sure that the server package is installed. Try:
sudo apt-get install openssh-server
If you install the meta-package ssh, both packages will get installed as well.

---

### Post by joenix on 2008-09-01
The 'Connect to Server' functionality under Gnome is provided by the Nautilus File Manager. Since you are using KDE, you probably won't have it installed, but I'm  pretty sure KDE's file manager has a similar function.

---

### Post by chronos00 on 2008-09-01
I should have read the thread's name started with [kubuntu] :-p

It seems the "connect to server" is not a separate program but is part of the gnome file browser named "nautilus". In fact, in nautilus you just go to "file"-> "Connect to server".

I'm telling you this because PERHAPS the KDE file explorer has a similar function under the "file" menu. You should check it out.

Another possibility is to use "gFTP", a program originally meant to access FTP sites that has extended functionality (eg, for SSH).

To install it just "sudo apt-get install gftp"

---

### Post by bobleny on 2008-09-01
Well, unfortunately, installing software on the desktop is out of the question....

Is there a way to pluck data from my desktop without installing new software?

---

### Post by joenix on 2008-09-01
Do you mean you are not allowed to install software on both the source and the target computer? That might be a bit tricky.

BTW, if you would like to connect to a SSH server from KDE, open the Dolphin file manager and enter the following location:
fish://server/path

where server is either the hostname or address of the server and path is the path of the directory you want to open.

---

### Post by chronos00 on 2008-09-01
You would only have to install gFTP where you want to copy the files TO (not where the data is stored).

In any case, if you can't install any additional software you will have to go the SCP way (which is not the easiest).

---

### Post by bobleny on 2008-09-01
Hey, thanks for all of you help, I finally figured it out!

I installed openssh-server on my laptop, with no issues.
Then from my desktop I typed:
```

scp -r /home/bob/Back_in_Black.mp3 bob@192.168.x.xxx:~

```

Next thing I know, I'm listening to AC/DC on my laptop!

Then to transfer files the other way:
From my desktop I typed:
```

scp -r bob@192.168.x.xxx:/home/bob/Hail_Caesar.mp3 ~

```

Next thing I know, I've got more AC/DC than I can handle! :guitar:


Thanks for all of your help, couldn't have done it with out you!


Cheer up, the worst has yet to come....

---

### Post by meganox on 2008-09-01
I'm surprised nobody has mentioned rsync in this thread...

---

### Post by retrovertigo on 2008-09-01
Ahh yeah, I didn't even think of rsync... which is odd since I use it often at work.  It's much more forgiving of connection interruptions and is perfectly suited for transferring large amounts of files.

---

### Post by bobleny on 2008-09-02
Well, if someone wants to... Feel free to explain how rysnc works.

My guess is, it works the same as scp, but maybe GUI based?

Being able to transfer files is great, perfect for now, actually. In the future though, It would be really awesome if I could access my desktop hard drive from my laptop just like opening a folder....

Thanks anyways!

---

