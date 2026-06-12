---
title: "[SOLVED] Root user issue"
date: 2008-09-29
forum: General Help
---

### Post by k3kiaze on 2008-09-29
My root access doesnt seem to have access to my user programs..etc. 

Please look at picture below to see what I mean. The window on the left is normal user access, you can see the theme I applied to the system. The window on the right is an output of "gksudo nautilus", clearly the root user uses some default scheme from somewhere.

The reason I need this fixed is because if I want to edit a text document with root access, it opens as a read-only. Someone please help me. Thanks.

[IMG]http://img100.imageshack.us/img100/6613/screenshotlg1.png[/IMG]

---

### Post by Peter09 on 2008-09-29
There is a couple of ways of doing this, I guess the most accepted would be

1. Open a terminal
enter the following line

sudo gedit <path to the file you want to edit>

The Path to the file will be the same as is shown in the top of the file manager window. It will look something like.

/etc/<filename>

beware of editing files in the system directories unless you are sure what you are doing.

---

### Post by cariboo on 2008-09-29
You should use gksu instead og sudo when using graphical applications, Press Alt-F2 then enter:

```
gksu gedit /path_to_document
```

For the reason why to use gksu instead of sudo see:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Jim

---

### Post by Aearenda on 2008-09-29
Regarding the root theme being different, themes are per-user, not per-system. If you have custom local themes for your user, they are not usable automatically to root or anyone else. The simple permanent solution I use to this when using 'gksudo', especially for synaptic etc, is to start a terminal session and enter the following commands [CAUTION: enter exactly as shown - you are on dangerous ground here, using 'sudo' in combination with 'rm']:
```

sudo rm /root/.themes/*
sudo rmdir /root/.themes
sudo ln -s ~/.themes /root/.themes

```

The first command here deletes the local themes files, and the second the themes folder for the root user. The third links your own themes folder so that root uses it as well. This way your user's custom themes are available to the root user. Now when you run 'gksudo gedit' to edit system files, you should still have your custom theme.

---

### Post by aysiu on 2008-09-29
What does the theme have to do with what files you edit?

Even if you don't have the same window look, the files and folders available for editing are the same.

---

### Post by Aearenda on 2008-09-29
It doesn't - I'm just answering the unanswered question implicit in > clearly the root user uses some default scheme from somewhere.but I forgot to say that!

My previous post is now edited to make this clear.

---

### Post by k3kiaze on 2008-09-29
First - Thank you for so many responses.

I don't really care what theme the root user has, but i was surprised that it was different to the system theme (i guess).

> gksu gedit /path_to_document

and 

> sudo gedit <path to the file you want to edit>

wont let me save the file either. (Read-only access). Looking at the picture below I think you'd say its a permissions issue, and this is also probably why the theme for root user is different. So I guess my question should have been: How do I repair root user permissions?

[IMG]http://img145.imageshack.us/img145/7981/screenshotwj2.png[/IMG]

---

### Post by Peter09 on 2008-09-29
Don't edit this file with anything but visudo - you risk all----

From the general discussion we have been having I would suggest you need to have more experience before editing this file.

What are you trying to achieve?

---

### Post by aysiu on 2008-09-29
The /etc/sudoers file is a special file you have to edit with the command ```
sudo visudo
```

---

### Post by k3kiaze on 2008-09-29
Just following instructions here: [http://www.fs-security.com/docs/faq.php]("http://www.fs-security.com/docs/faq.php").

Are there any links for noobs on usage of visudo, so i know how to save after editing? And does this mean I **don't** have to repair permissions?

---

### Post by Excalibre on 2008-09-29
> **k3kiaze said:**
> And does this mean I **don't** have to repair permissions?
I'm betting no. I've never altered that file myself, but it's hard to imagine things going so wrong that root didn't have access to modify system files.

Regarding the themes thing above, you're right about it being because root doesn't have the same themes, but I think they do it that way on purpose. It's nice having a visual reminder to be careful because an app is running with root access. Most file managers will even display a special message at the top to remind you.

---

### Post by bodhi.zazen on 2008-09-29
root uses /root as a home directory.

Settings / icons are stored in the dot or hidden files there.

If you change your settings when you are running an X app as root on a X session where you are running as a user, as in the OP original post, your settings will be saved to your user's home and your will then have permissions problems.

Thus, when running X applications as root, use gksu to prevent this problem. ;)

---

### Post by k3kiaze on 2008-09-29
Thanks for the info. As an update, I find that the included (default) themes apply to both me (user) and root. It's only the custom themes i install that change root theme to the same grey standard theme. So it seems that root can't get access to the themes i install.

I really don't care what theme root uses and as you say > It's nice having a visual reminder. I was only worried that my permissions may be messed up. If visudo is the only way to edit that file then so be it.

---

### Post by TeXtonyx on 2008-09-29
I forget why I edited with visudo. But I was quite surprised to find that the default editor
was vi. It was easier to read a short tutorial on vi than to find out how to change the editor.

---

### Post by k3kiaze on 2008-09-29
Followed [these]("http://maeks84.wordpress.com/2008/05/29/how-to-use-visudo/") instructions, but was painful and stressing to get it to work. Now its done and I never want use vi anymore. Thanks to all for solving this.

---

