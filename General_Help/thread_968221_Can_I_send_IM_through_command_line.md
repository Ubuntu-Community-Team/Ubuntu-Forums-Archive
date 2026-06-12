---
title: "Can I send IM through command line?"
date: 2008-11-02
forum: General Help
---

### Post by orduek on 2008-11-02
Hi,
I use Pidgin with ICQ account to send SMSs.
I would like to know if I can use it through command line (so I could get it into a script that send automatically SMS)?

---

### Post by PCessna on 2008-11-02
> **orduek said:**
> Hi,
I use Pidgin with ICQ account to send SMSs.
I would like to know if I can use it through command line (so I could get it into a script that send automatically SMS)?

I am not too sure of this, But my best shot would be there would be a IMing application to do so, Infact I think I've heard of it, Not sure though, sorry.

---

### Post by orduek on 2008-11-03
any ideas?

---

### Post by JDorfler on 2008-11-03
I believe Gaim in your repositories is the terminal im client that pidgin is based on.

---

### Post by kilroy423 on 2008-11-03
> Hi,
I use Pidgin with ICQ account to send SMSs.
I would like to know if I can use it through command line (so I could get it into a script that send automatically SMS)? 

Finch is a console-based IM program that lets you sign on to AIM, Jabber, MSN, Yahoo!, and other IM networks. It runs on Unixes. It uses GLib and ncurses. 

[http://developer.pidgin.im/](http://developer.pidgin.im/)

[http://developer.pidgin.im/wiki/Using%20Finch](http://developer.pidgin.im/wiki/Using%20Finch)

good luck

---

### Post by ad_267 on 2008-11-03
Finch is the command line version of pidgin.

Edit: I was too slow.

---

### Post by orduek on 2008-11-03
But I didn't find an option to send IM through one line command with finch (so I would be able to put it in a script).
anyone knows how?

---

### Post by sica07 on 2008-11-03
I don't know if this is the answer you're looking for, but look at this (centerim is just another IM client for terminal): [http://www.centerim.org/index.php/Frequently_Asked_Questions#Can_i_use_CenterIM_to_use_messages_from_within_another_shell_script.3F](http://www.centerim.org/index.php/Frequently_Asked_Questions#Can_i_use_CenterIM_to_use_messages_from_within_another_shell_script.3F)

---

### Post by Portmanteaufu on 2008-11-03
I don't know about using libpurple to do it (though I'm sure you could -- it's a very complete library), but you can send SMS messages by e-mail and e-mailing with a one-line command is really simple.

Read here to get the list of address formats you should use to send SMS messages to the different carriers: 

[http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/](http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/)

To actually send the email, look into sendmail /postfix or one of the SMTP modules for perl / python.

---

### Post by Portmanteaufu on 2008-11-03
Here's the [man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mail") for mail, which can send the actual e-mail.

---

### Post by orduek on 2008-11-03
> **Portmanteaufu said:**
> I don't know about using libpurple to do it (though I'm sure you could -- it's a very complete library), but you can send SMS messages by e-mail and e-mailing with a one-line command is really simple.

Read here to get the list of address formats you should use to send SMS messages to the different carriers: 

[http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/](http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/)

To actually send the email, look into sendmail /postfix or one of the SMTP modules for perl / python.

My problem is that I'm from Israel - thus, don't have a phone carrier thats on that list.
This is why I'm searching how to do it through Pidgin/Finch/Empathy etc.
Unless I can find my carrirer smtp.

---

### Post by orduek on 2008-11-04
anyone?

---

### Post by blazercist on 2008-11-04
sudo apt-get install naim

---

### Post by orduek on 2008-11-05
> **blazercist said:**
> sudo apt-get install naim

can I use it with one command?

---

### Post by blazercist on 2008-11-05
No, its an application that runs in terminal, if you are looking for a binary that you can pass switches to in order to send messages (e.g.: #$: sendmsg [screen name]  [message body]) I don't think its possible.

---

### Post by Portmanteaufu on 2008-11-05
One way to go about doing this would be to have Pidgin already running and use the dbus interface they provide to send the message. Then you could do
```

sendmsg [username] [message body]

```
and it would just use the already running pidgin session.

---

### Post by orduek on 2008-11-05
I tried that with no success.
it says I have no SAFT server or something like this.
if it will be possible to send through command line (when pidgin is on) it will be great.
I think the problem is that it tries to send through the computer name and not through pidgin.
can I change it?

---

### Post by blazercist on 2008-11-05
> **Portmanteaufu said:**
> One way to go about doing this would be to have Pidgin already running and use the dbus interface they provide to send the message. Then you could do
```

sendmsg [username] [message body]

```
and it would just use the already running pidgin session.

This is possible unless of course you are running a CLI environment then you can't run pidgin at all because there's no X server.  Also, though possible (if running X  I don't see how it would be useful because it would be much simpler to use the GUI, unless you are going to script a mass messager or something like that.

---

### Post by Portmanteaufu on 2008-11-05
As far as I know, Finch, Pidgin's terminal equivalent, still has the dbus interface exposed and obviously doesn't require X -- you could run finch as a background process and still use the same general idea.

If even *that* is too much, then you're pretty much going to have to write your own script to use libpurple to log into AIM, send the message and log out. Of course, if you do that, you'll be limited to how frequently you can run the script as AIM and others have limits on logins.

---

### Post by Portmanteaufu on 2008-11-05
By the way, I shouldn't have used "sendmsg" as my example program name. That's an actual program and I wasn't recommending it. In my example, "sendmsg" was intended to represent a program that you had written to send the desired message using dbus.

Sorry for the confusion!

---

### Post by orduek on 2008-11-05
OK.
Does anyone has some program for example, I'm not a programmer or the like.
Thank you.

---

### Post by Portmanteaufu on 2008-11-05
You can see a bunch of dbus examples using Python [here.]("http://developer.pidgin.im/wiki/DbusHowto")

You'll probably want to look at the section entitled "Calling Pidgin Methods". The function for sending an IM is "PurpleConvImSend".

---

### Post by Altay_H on 2010-10-08
I was looking for the solution to this exact topic and didn't find it anywhere. I finally figured it out myself, so if anyone else is looking for it, here's the script:
```
#!/usr/bin/python
import sys, dbus, gobject;
bus = dbus.SessionBus()
obj = bus.get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
purple = dbus.Interface(obj, "im.pidgin.purple.PurpleInterface")
for conv in purple.PurpleGetIms():
	user = purple.PurpleConversationGetName(conv)
	if len(sys.argv) == 1:
		print user
	elif user == sys.argv[1]:
		purple.PurpleConvImSend(purple.PurpleConvIm(conv), sys.argv[2])
		print 'Sending "'+sys.argv[2]+'" to '+sys.argv[1]
```

Save the script and run it with two command line arguments like so:
script.py "username" "message"

If you run it without any arguments, it will print out a list of all available recipients. It is only able to send messages to buddies if you already have a chat window open.

Note that it requires X to run, so if you're running it as a cron job or through SSH you'll need to run it this way:
DISPLAY:=0;export DISPLAY;script.py "username" "message"

---

