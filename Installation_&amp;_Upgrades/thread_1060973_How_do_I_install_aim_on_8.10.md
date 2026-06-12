---
title: "How do I install aim on 8.10?"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by theblackred on 2009-02-05
Pidgin is ok but I want to be able to video chat with aim. I downloaded the tgz file from aim [http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)
And I found the directory and typed gunzip -c aim-1.5.286.tgz | tar xvf - into the terminal but it came up with the error:

dan@cutie:/tmp$ gunzip -c aim-1.5.234-1.i386.tgz | tar xvf -
./
usr/
tar: .: Cannot utime: Operation not permitted

*all the files in the aim folder*

tar: Error exit delayed from previous errors

Help would be appreciated.

---

### Post by ibutho on 2009-02-05
I don't think you should bother yourself with that package. Its old and there are better IM clients installed by default in most Linux distros. Pidgin should be already installed on Ubuntu. It supports AIM, MSN, IRC, YAHOO etc.

---

### Post by theblackred on 2009-02-05
I know everyone here thinks pidgin is better. 
From what I've seen, it does most of what aim does, which is the only IM service I used, but it doesn't do video chat.
I just want aim so I can video chat since it doesn't look Pidgin will ever have that feature. 

Thanks for reading my first post and really trying to help me. [/sarcasm]

So can anyone help me install it?

---

### Post by ibutho on 2009-02-05
Well, I was trying to help you, so the sarcasm doesn't help. The AIM client for Linux does not support video. Like I said its an old app and its not been maintained for years. If you want to install it, go ahead and knock yourself out.

---

### Post by theblackred on 2009-02-05
Ok I'll try Wine I guess.
Thanks for specifying what you meant by old, I thought you meant aim itself was old, not the version for ubuntu.
I apologize for my sarcasm, but I was irritated you responded that aim isn't worth it without giving an alternative program to for video chat, so I assumed you responded without reading my first post.

---

### Post by ibutho on 2009-02-06
You may want to also look at [Empathy]("http://live.gnome.org/Empathy"). it has video support for some im protocols, but I am not sure about AIM.

---

