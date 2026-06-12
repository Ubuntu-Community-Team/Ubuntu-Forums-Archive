---
title: "installing DSL connection"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by taurus28 on 2009-05-05
Just installed Ubuntu 9.04 without trouble.  New user so I am rather floundering. How do I install a DSL connection?  It will recognize the disc but when I try to start the install program it says it can't handle it.  Can anyone offer some help?

Taurus28

---

### Post by pastalavista on 2009-05-05
Your disk was made for Windows. You shouldn't need to install anything to connect to DSL. Just set it up with the Network Manager in the upper right panel.

---

### Post by taurus28 on 2009-05-06
Thank you. There is no Network Manager showing upper right. Perhaps it is because my screen is not showing full screen. There is about an inch of black on the left side and I don't seem to be able to change it.

Any further instructions would be appreciated.

Taurus28

---

### Post by Kareeser on 2009-05-06
Assuming your modem is in bridge mode (that is, it allows the computer itself, or a router to handle establishing the link, you'll have to modify the network settings.

Press Alt-F2 and type in "nm-connection-editor". You can set up the DSL connection from there under the "DSL" tab.

---

### Post by taurus28 on 2009-05-07
Thanks: Followed instructions but I got the message "no such file or directory" Any suggestions as to what I do now?

taurus28

---

### Post by Kareeser on 2009-05-07
Really? That should've been installed automatically.

What version of Ubuntu are you using? (type "lsb-release -a" at the terminal)

If at all possible, try to install that program using apt-get
```
apt-get install nm-connection-editor
```

---

### Post by taurus28 on 2009-05-08
Thanks again: My version is Nautilus 2.26.2 . I followed your instructions and got the same results as before. I am likely doing something wrong, but have no idea what. Any added help would be appreciated.

Taurus28

---

### Post by Kareeser on 2009-05-08
Oh!

Nono, type this into a terminal, and the dialogue should pop up.

Either open the terminal by pressing Applications -> Accessories -> Terminal, or alternatively, "Alt-F2".

Once there, try "nm-connection-editor"

---

### Post by taurus28 on 2009-05-09
Thanks again: This time it worked. result is auto etho. One other thing , I don't seem to be able to shut down except by the power button. What am I missing?

Taurus28

---

### Post by taurus28 on 2009-05-12
Figured out the shut down problem Ctl Alt Del seems to work.

Still need information on the DSL install though.

Taurus28

---

### Post by Kareeser on 2009-05-13
It's not the "result" you're looking for. When you type "nm-connection-editor" in the terminal, you need to also press the "DSL" tab in that window. You can set up your DSL from there.

---

### Post by taurus28 on 2009-05-14
Sorry, I guess I am being a little dense. Perhaps I am not inputting the right info. If I may, let me run through them.

Connection Name   what is required?

User Name    the name that I sign in with

Service      Is this DSL?

Password    obvious

When I click on Connect to Server.

Service Type ( My service is 295.dsl)  is this what goes in?

Location URi  What goes in here?


Perhaps if I do these right I will be all set.


Thanks I appreciate your help.

Taurus28

---

### Post by Kareeser on 2009-05-14
I believe all you need to connect is the username and password. Input those two in their respective boxes, as the ISP has given to you, and try to connect.

Not having done this before, I don't exactly know how Ubuntu handles the connection, but I think you can connect by left-clicking the network icon in the notification area.

---

### Post by taurus28 on 2009-05-14
Thanks so much Kareeser.

I have finally managed to connect.  It was as you said in addition to inputting PPPOE in the Service box.  Thanks again I will undoubtably have many more questions before I am familiar with everything.

Taurus28

---

