---
title: "Not sure where to go now"
date: 2008-09-17
forum: General Help
---

### Post by xmango on 2008-09-17
I am a complete newbie to linux and I am trying to set up my own personal server as a way to learn.  I am using the latest version of Ubuntu Server and want to keep the GUI off of it.  I follow what I find in the forums here but I have this basic question =x

When I run a command such as vi /etc/apt/sources.list to edit my update source list, I understand how to edit it and how to comment out of thing, but what do I do next apart from reset my system (which I am not sure saves anything).  No command line bar is there and I cant do anything else.

Any help would be appreciated.

/xmango

---

### Post by danielcburton on 2008-09-17
> **xmango said:**
> I am a complete newbie to linux and I am trying to set up my own personal server as a way to learn.  I am using the latest version of Ubuntu Server and want to keep the GUI off of it.  I follow what I find in the forums here but I have this basic question =x

When I run a command such as vi /etc/apt/sources.list to edit my update source list, I understand how to edit it and how to comment out of thing, but what do I do next apart from reset my system (which I am not sure saves anything).  No command line bar is there and I cant do anything else.

Any help would be appreciated.

/xmango

to re load your sources.list after editing and saving do the following.

```
sudo apt-get update
```

---

### Post by xmango on 2008-09-17
Thanks for the reply :)

So do I type sudo at the bottom of the page, or anywhere?  I am used to the command line being there, so when it is not I get scared lol!

I have tried to type over commands when there, and nothing seems to happen. Any Ideas?

---

### Post by rsambuca on 2008-09-17
Are you sure that you are exiting vi properly?  After closing vi, you should obviously be back at the command line prompt.  Something is not working properly on your system.

---

### Post by xmango on 2008-09-17
To clarify a little more, how do I save what I have finished editing?

Sorry for the stupid questions :(

---

### Post by danielcburton on 2008-09-17
> **xmango said:**
> Thanks for the reply :)

So do I type sudo at the bottom of the page, or anywhere?  I am used to the command line being there, so when it is not I get scared lol!

I have tried to type over commands when there, and nothing seems to happen. Any Ideas?

oh your still in the file
```

press esc. :wq enter
```

This should save the file. If you get an error about cant save you need to ```
sudo vi /etc/apt/source.list
``` then make you changes

---

### Post by xmango on 2008-09-17
Ah ha!  Thank you.  I shall switch over and try that.  Thanks for your help

/xmango

---

### Post by rsambuca on 2008-09-17
That's why I use nano for command line editing.  I don't have to memorize all of these crazy vi commands. :)

---

### Post by whizbaby on 2008-09-17
Is the problem that you dont know how to do 'save' in vi? You type ```
:w
```
to leave vi type ```
:q!
``` 
But in my opinion vi is dangerous to someone new, as it is really easy to break things by just hitting the wrong key. Of course this is the same with all other editors, so let me show you an example to illustrate:
admin Naab is new and wants to re-edit the dhcpd.conf, because he realised that he forgot to change the serial number. He then forgets to hit 'i' (INSERT mode of vi to edit a file) and starts inputting his number '2..0..'. After two digits he realises that he forgot hitting 'i' and does it then, types in the serial number and does ':wq!' which means 'save and leave'. What now really happened is that the number he put in is there 20 times in succession now and so is way too big and completely wrong. If Naab doesnt realise that and restarts the dhcpd the network might be broken for a while.
Powerful editors have powerful features that require reading quite a part of the manual and using the with text/code for a while before doing administrative tasks with it^^
Just use nano or jed first, two very simple editors which are unlikely to do weird stuff like emacs or vi. Get to know the power-ed of your choice and switch to that if you feel confident using it. 
In my opinion emacs is the better solution when you have no GUI because you can really do anything in it and simple text editing is quite intuitive (unlike the 'mode' approach of vi). Dont get me wrong, vi is a great edior, only I prefer emacs.
EDIT:
ps: aww you are all so fast its solved when I posted mine -.-

---

### Post by danielcburton on 2008-09-17
amen!!!! VI is dangerous if you dont know it

---

### Post by Nameless_one on 2008-09-17
...but addictive if you do.

---

### Post by whizbaby on 2008-09-17
[SPAM]
Wanna fight vi vs emacs 1 on 1?
[/SPAM]
*[SIZE="1"]due to his expirience in the past whizbaby marks this message as not to be taken serious[/SIZE]*

---

