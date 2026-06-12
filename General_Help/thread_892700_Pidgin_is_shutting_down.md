---
title: "Pidgin is shutting down"
date: 2008-08-17
forum: General Help
---

### Post by Deldo on 2008-08-17
Hello :-)

I got a problem again.
It is about Pidgin. When I open it and I write to somebody, adding a friend or do nothing, it shuts down after maybe 1 or 2 minuts. I don't know what is wrong. I have the newest version of ubuntu and pidgin. I don't get any error message or anything. It just closes.

I not sure, but I couldn't find a similar problem on the forum.
So can anyone help me?

Rune Eriksen

---

### Post by Naatan on 2008-08-17
Start pidgin from the terminal with the debug flag

$ pidgin --debug

Then wait for it to crash and check the terminal for the error message it gives.

---

### Post by Deldo on 2008-08-17
With the debug flag? I don't know what it is.

---

### Post by Naatan on 2008-08-17
Open your terminal and type

pidgin --debug

Then press enter

"--debug" is the debug flag.

---

### Post by Deldo on 2008-08-17
I think it is this:

(22:07:16) facebook: got new messages: for (;;);{"t":"msg","c":"p_537254042","ms":[{"type":"notifications_read"},{"type":"notifications_read"},{"type":"notifications_read"},{"type":"notifications_read"},{"type":"notifications_read"}]}
(22:07:16) facebook: type: notifications_read
Segmentation fault

---

### Post by Naatan on 2008-08-17
Check the following thread 

[http://ubuntuforums.org/showthread.php?t=880596](http://ubuntuforums.org/showthread.php?t=880596)

---

### Post by Deldo on 2008-08-17
I will give it a go.
I actually fixed the problem.
I have a MSN account, AIM and installed the plugin for Facebook chat. If i disable mt Facebook and AIM account, it doesn't shut down.

---

### Post by Deldo on 2008-08-17
I didn't work. :-/

---

### Post by Naatan on 2008-08-17
Did you follow the steps in the thread I gave you?

---

### Post by Deldo on 2008-08-19
Yes, I did. :)

---

### Post by Naatan on 2008-08-19
You have disabled all audio in pidgin then? When I search google this is the issue that keeps popping up..

Try installing the package pidgin-dbg

$ sudo apt-get install pidgin-dbg

And then run pidgin with the debug flag again

$ pidgin --debug

It should give more debug information.

Also, if you are using multiple accounts on Pidgin, try disabling them all and then enable them one by one while testing each one for a couple of minutes to see if Pidgin crashes before enabling the next.

---

### Post by pigphish on 2008-10-28
i have a similar problem. As soon as I message anyone it abruptly shuts down. 

The last line in the console after running pidgin --debug is:
Segmentation fault


any thoughts?

---

### Post by Queue29 on 2008-10-28
> **pigphish said:**
> 


any thoughts?

Try Empathy. Takes a bit of effort to get it installed, though a bit of googling works wonders.

---

