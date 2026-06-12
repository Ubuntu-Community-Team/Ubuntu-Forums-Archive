---
title: "[SOLVED] Run a program on startup"
date: 2008-08-25
forum: General Help
---

### Post by Mailme on 2008-08-25
My system;
Ubuntu Terminal 8.04.1

I'm trying to run a program when the PC powers up. I want the program to run as a user, but that user doesn't log in all the time, BUT I still want the program to run. How do I do this please?


Thanks.

---

### Post by Ryadt on 2008-08-25
You can launch programs at startup by adding them in Preferences > Sessions.

---

### Post by forger on 2008-08-25
..or you could read up on how to set up the application in crontab:
```
man crontab
man 5 crontab
```

```
sudo crontab -u someuser -l
sudo crontab -u someuser -e
```

---

### Post by caljohnsmith on 2008-08-25
To run your command(s) as another user, you could use something like:
```
su -c "command1;command2" <username>
```
Now if you put that in your System > Preferences > Sessions, the problem with that is it needs to ask you for <username>'s password. But if you run the above command while you are root, it won't ask for <username>'s password. 

Therefore, I think you can solve your problem by putting the above command in /etc/rc.local, because everything in that script is run as root on startup:
```
gksudo gedit /etc/rc.local
```
At the bottom, before the exit line, just add the su command above with whatever commands (command1, command2, etc) you want to run as <username>. Let me know how it goes. :)

---

### Post by forger on 2008-08-25
cool, didn't know that :)

---

### Post by Mailme on 2008-08-25
No, that doessn't work - it still waits for the USERS password.

What I'm trying to do is set up VLC to run as a user because it complains when run as root. (I've set VLC as a video server.)

The cmd I want to run is;

vlc -I http --http-host 192.168.1.120:8080 &&

Remember I'm in a non-gui i.e. terminal

Trying to run your idea as ROOT produces the following error;
su -c "vlc -I http --http-host 192.168.1.120:8080 &&" <username>
bash: -c: line 1: syntax error: unexpected end of file

---

### Post by caljohnsmith on 2008-08-25
> **Mailme said:**
> No, that doessn't work - it still waits for the USERS password.

What I'm trying to do is set up VLC to run as a user because it complains when run as root. (I've set VLC as a video server.)

The cmd I want to run is;

vlc -I http --http-host 192.168.1.120:8080 &&

Remember I'm in a non-gui i.e. terminal

Trying to run your idea as ROOT produces the following error;
su -c "vlc -I http --http-host 192.168.1.120:8080 &&" <username>
bash: -c: line 1: syntax error: unexpected end of file
You are putting && at the end of your command, so the shell is looking for another command after that. That is why you get that error. If you want to run the process in the background, you should use & and not &&.

---

### Post by mssever on 2008-08-25
> **Mailme said:**
> su -c "vlc -I http --http-host 192.168.1.120:8080 &&" <username>
bash: -c: line 1: syntax error: unexpected end of file
It's an error to end a command with &&. Did you mean ```
su -c 'vlc -I http --http-host 192.168.1.120:8080' username &
```This, or course, goes in /etc/rc.local or something along those lines.

---

### Post by Mailme on 2008-08-25
This worked;

su -l <username> -c "vlc -I http --http-host 192.168.1.120:8080" &


Many many thanks.

---

