---
title: "Easy ftp server install ?"
date: 2005-11-07
forum: General Help
---

### Post by stack445 on 2005-11-07
I"ve try pro-ftpd, pureftpd, vsftpd, and i can say that they are not easy to configure. Is there something like serv-u ftp for linux. I meen all gui and no fooling around 7 different config file just for a ftp server.  I just want a ftp server that is very easy to configure, to start and to stop. any idea ?

---

### Post by frodon on 2005-11-07
There is one GUI for proftpd called gproftpd, but i don't advice it since you have to run the GUI as root to be able to handle the server and therefore the config file. So you can easily destroy your proftpd config and also create a configuration which isn't enough secure.
I used also FTP serv-u when i used windows before ubuntu and now i use proftpd, it's not such difficult to configure, there is a command to see the persons who are connected on your server and what files they download or upload.
In addition i wrote a small script with a GUI (using zenity) to start/stop, mount some directories and show your IP.
So if you're interested i wrote a guide to do that and also gave my script in my [HOWTO]("http://ubuntuforums.org/showthread.php?t=79588")
If you get some problems setting your proftpd server i can help you.

good luck ;)

---

### Post by stack445 on 2005-11-07
I've pretty much follow your howto except for some stuff.  Now when i try to start proftpd, instead of beiing in to /etc/init.d/proftpd, it's in /usr/sbin/protfpd ? 
And whe i try to log in localy that what i got :

root@cortex:/usr/sbin# ftp localhost
Connected to localhost.localdomain.
500 FTP server shut down (going down at Mon Nov  7 12:45:06 2005) -- please try again later
ftp>

any idea ?
Here is my config :


 #
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "cortex"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 300

DisplayLogin                    welcome.msg
DisplayFirstChdir .message
ListOptions "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

DenyFilter                      \*.*/
DefaultRoot /data/video/ !maxime
# DefaultRoot /



ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log


UseFtpUsers on

# Port 21 is the standard FTP port.
Port                    21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 3

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on
PersistentPasswd                off

---

### Post by frodon on 2005-11-08
Are you sure that the "sudo /etc/init.d/proftpd start" command don't work ? it's really weird since proftpd is a service and inetd manage the services. This command must work, if not you have an installation problem.
By the way, i think you didn't give me the whole proftpd.conf file.
Also if you changed or don't follow some steps of the howto you must tell me if you want me to be able to answer because i can't guess what you changed ;)

Don't worry it will work ;)

---

### Post by stack445 on 2005-11-08
I do seem to have a installation problem because there is no proftpd in init.d. I do remember that is was there the first time i did install it. It was working before i ha to make some config change ( nothing to do with ftp, just a re-organistion of data) 

The change i made from your config exemple is as follow: 

on port 21, i dont used useralias, each user is chrooted in the /data/video folder exept one. That is about it. And yes the entire config file is there in my post, you seem to imply that there is something missing ? 

And by the way, do you speek french ( just to know, seem you comme from france) 

Ca serai plus pratique de communiquer en francais, dans le forum francais bien sure ! 
:D 

merci

---

### Post by frodon on 2005-11-08
Ok, why not, give me the link to the french forum if you have posted something in or if you prefer use mail send me your email by PM.
Endeed it will be easier ;) , however when your problem will be solved it would be good to write the solution here in case that other users get the same problem.

Useralias is important to prevent telnet access, and also the it could be really unsecure to not lock a user in his home directory. If your goal is to create special user only for you who is able to access the whole computer there is another way (more secure) to do it.

Donc envois moi ton email ou donne moi un lien si tu as poste dans le forum francais et je continuerai de t aider en francais ;)

---

