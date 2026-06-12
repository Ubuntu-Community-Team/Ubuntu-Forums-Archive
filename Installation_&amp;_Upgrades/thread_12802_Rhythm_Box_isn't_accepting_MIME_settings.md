---
title: "Rhythm Box isn't accepting MIME settings"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by Eejay on 2005-01-26
I tried using this command(sudo apt-get install gstreamer0.8-mad) to enable mp3 support in Rhythm box and received the error message pasted below 
username@linux:~ $ sudo apt-get install gstreamer0.8-mad
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gstreamer0.8-mad
username@linux:~ 





Then this error when downloading a video

There is no element present to handle the stream's mime type audio/mpeg.

I've been dying to get this thing up and running just cant seem to figure out the problem.

Any suggestions on how to correct this error will be very much appreciated

---

### Post by Buffalo Soldier on 2005-01-26
I think gstreamer0.8-mad is in the universe repository. How to add a repository to your apt-get source list? Look here [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

And after that I would suggest you install gstreamer0.8-plugins. This package will ensure that all GStreamer plugins are installed.

```
sudo apt-get install gstreamer0.8-plugins
```

---

### Post by Eejay on 2005-01-27
Thank you for responding to my message

I copy/ pasted and manually typed sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup into the command terminal about 20 times  an error message pops up saying bash command  not found
Is it possible that Rhythm box is already installed and the only thing needed is the plug ins


Sorry for being such a Noob

---

### Post by Buffalo Soldier on 2005-01-27
First, yes Rhythmbox is already installed and u only need the right plugin to play mp3 files. That's where **sudo apt-get install gstreamer0.8-plugins** comes in.

Second, I copied and pasted **sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup** into my terminal and it is working fine.

I really wish I can help you more. But so far that's the solution I know. Probably some else can help you more. The community in here is great, just ask politely and most would be eager to help you :)

---

### Post by Eejay on 2005-01-27
[QUOTE=Buffalo Soldier]First, yes Rhythmbox is already installed and u only need the right plugin to play mp3 files. That's where **sudo apt-get install gstreamer0.8-plugins** comes in.



[/QUOTE]

Thanks for the help Buffalo hunter
Rhythm box is up and running 

That's the code the terminal needed to to make it work 

Just had to keep opening and closing the terminal 20 or so times to get the terminal to recognize the code  :)

---

