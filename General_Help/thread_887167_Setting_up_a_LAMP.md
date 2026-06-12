---
title: "Setting up a LAMP"
date: 2008-08-11
forum: General Help
---

### Post by Dhekke on 2008-08-11
Hi,
I'm trying to set up a LAMP server just to play around with PHP.
I decided, as training, to get Apache, MySQL and PHP from source, and it went bumpfully well. 

But now I got two questions:

After the MySQL installation, I tried to add the apache2 and mysql folders to the system paths adding
```
export PATH=$PATH:/usr/local/mysql/bin
export PATH=$PATH:/usr/local/apache2/bin
```
at the end of the bashrc file. And now when I call httpd (for instance) it finds the right path, but httpd asks for root privileges. When I use sudo I get
```
gabe@desktop:~$ sudo httpd -k start
sudo: httpd: command not found
```
If i use **sudo su** (or **sudo -s** or **sudo -i**) before calling httpd, though, it works and httpd starts.
Here's the $PATH
```

root@desktop:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/mysql/bin:/usr/local/apache2/bin

```

So, what do I do about it?


The second question is more specific, and not necessarily a problem, but whenever I start MySQL i get
```

root@desktop:~# mysqld_safe --user=mysql &
root@desktop:~# nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /usr/local/mysql/var

```
and then it just kinda freezes there. Until I press enter and it goes back to bash. But sometimes it doesn't go back even after a long time, so I just close the terminal window.
Is this normal? and byt the way, what's that nohup alert I get? It doesn't stop the mysql, but what does it mean?

thanks a lot

---

### Post by rhodry on 2008-08-11
I don't know that I can be of too much help with your specific queries.

The 1st one sounds like an "environment" issue I think. I think 'sudo' gives you the user super power but retains your user environment, whereas running specifically as the super user gives you 'root's environment. I think that changes the PATH being utilised? Try 'info sudo' command in a terminal. I have no idea on the MySql query.

What I wanted to mention though, was that [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) contains excellent guidance on setting up a LAMP server as both a stand-alone server or just for home web development. I have followed both and they work flawlessly.

Cheers,
rhodry.

---

### Post by Dhekke on 2008-08-11
shameless bump :(

---

### Post by djrobthaman on 2008-08-11
I'm not sure if I can be of any real help, but I'm running a local LAMP server on my system and I'm curious as to why you wanted to add apache and mysql to the system path after the installation.  I know... it's probably really obvious... go easy on me :)

---

### Post by Taxman415a on 2008-08-12
I also don't know why you would try to add those to your system path. I'm no sysadmin, but I know they have their own way to run them and I don't think that's it. :)

For your nohup question, you have some reading to do. :) Basically nohup "daemonizes" a process or allows it to run even after you have logged out. If you read 'man nohup' it will talk about making a process immune to hangups which normally happens when you logout of a shell, tty, or terminal that you run a process from. The rest of the message is about stderr and stdout, two of the three standard unix text data streams. In the unix shell paradigm programs take text input from the terminal or a pipe, etc and that's standard input (stdin), and then give their standard output (stdout) and any errors are sent out on a different stream, standard error (stderr). So that message is just being explicit about what's happening to stderr. Overall the message is basically telling you the command you ran invoked nohup and the rest is the message nohup is reporting.

I'm also no command line guru so I'm not sure exactly why it's hanging for you, especially since you're giving it the command to run in the background. Maybe that's conflicting with nohup ignoring input? But that doesn't really make sense, hence why I'm at a loss there.

Anyway, for your reading pleasure:
```
man nohup
```
[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)
[http://en.wikipedia.org/wiki/Standard_streams](http://en.wikipedia.org/wiki/Standard_streams)

---

### Post by Dhekke on 2008-08-12
Thanks for the info!

I wanted to add them to the system path so i could use just
```
httpd -k start
```
for instance, instead of having to type the whole path everytime i wanted to do something.
The installations from source didn't do this for me, like a package one probably would (or so I've heard).

And yes, I read the installation guides on ubuntuguide, but I wanted to practice my Linux skills, which aren't nearly as strong as they should :)

What I found on the sudo command is exactly what **rhodry** said. And I read that you could either recompile sudo (which i really won't do) or add a Defaults env_keep = "PATH" to the sudoers file...
I tried doing that through visudo, but it still doesn't work

---

