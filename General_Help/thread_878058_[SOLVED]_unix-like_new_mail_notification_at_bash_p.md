---
title: "[SOLVED] unix-like new mail notification at bash prompt"
date: 2008-08-02
forum: General Help
---

### Post by linfidel on 2008-08-02
I installed postfix/mailx so I could get email from the system from programs like cron, etc.  This is working fine, but I have to type "mail" at the bash prompt to see if there is mail.

In the bash docs, it tells how to set the variables MAILCHECK and MAILPATH to automatically check mail, like the unix systems, that print "You have mail" before the prompt.  So, I set it up, and I'm pretty sure it's correct, as it's pretty basic.  
MAILPATH=/var/mail/marty?"You  have  mail"
MAILCHECK=60
There is mail in the spoolfile in /var/mail/marty, but I don't get any notification.  I also tried setting MAILCHECK to zero, which I think tells bash to check before every prompt.

Is there something else I need to do?  Should this work?

Thanks,

---

### Post by cmnorton on 2008-08-05
Interesting. I use sendmail, and am only notified that I have mail if I enter mail at the command line. Yet, if I telnet into localhost, MAIL is set to my mailbox /var/mail/<my-mailbox> and I am notified of mail as soon as it arrives. If I add export MAIL=/var/mail/<my-mailbox> to .bashrc that does not give me instant notification.

I've looked at different environment files, and have not quite figured out the differences.
----------------------------------------------------------------------------------------------------------------------------------
Edit:

1) I made sure my terminal was set to something. In my case it was vt100.
2) Then, I made sure export MAIL=/var/mail/<my_username>
3) I then export TERMCAP=/etc/termcap.RHEL3, but this is my own file that I have kept from a Red Hat 9 system, because the settings worked perfectly with my Informix forms applications.

---

### Post by cmnorton on 2008-08-05
I am attaching my termcap file. Ubuntu handles terminfo differently, and there is a README in /etc/terminfo. You might get the same results following the instructions there.

edit:
the termcap file is too big. I cannot attach it.

edit 2:
---------

This might work in place of the TERMCAP environment variable.
 export TERMCAP=/usr/share/terminfo/v/vt100

---

### Post by ibuclaw on 2008-08-05
I know when you log into one of the tty terminals, it tells you whether or not you have any mail...


You could try a script which checks for the size of the mail file.

```

while true
do if [ -s /var/mail/marty ]
   then zenity --info --text="You have mail!"
   fi
   sleep 15m
done

```
And perhaps put it in your startup scripts...

Regards
Iain

---

### Post by geirha on 2008-08-05
I tried this with the following in a terminal
```
export MAIL=/var/mail/$USER
export MAILCHECK=10
```

Then in another terminal: ```
echo "test mail" | mail -s "test mail" $USER
```

Hitting enter to just get a new prompt a few times in the first terminal gave me the message "You have new mail in /var/mail/...". I believe it checks the timestamp of the mbox at the time MAILCHECK is set, and then alerts you whenever that timestamp changes, so you shouldn't get a notice about mail you've received before that.

It also worked with MAILPATH instead of MAIL.

---

### Post by linfidel on 2008-08-05
It seems that the terminal you run in X isn't a real login terminal like the TTY VTs or via ssh.  I'm pretty sure I can do something to accomplish what I want.

I know - I'll create a cron job to check my mailbox, and send an email if there is mail.  Wait...  uh, oh.  Never mind.  :)

I heard that evolution has an option to check the mbox mail.  I wonder if my regular email client, Thunderbird has that option?  I'll look into that.  It would be a good alternative if it's too hard to get the terminal idea going.

geirha:  did you use an x-windows terminal or a virtual TTY terminal?

Thanks to all for the input.  I'm not at home now, so I can't really do anything yet.

---

### Post by geirha on 2008-08-06
I used gnome-terminals.

---

### Post by linfidel on 2008-08-06
Well, I found that Thunderbird did work with this, and I was able to set it up to read my mail spool, so that will probably work out the best for me, since I use it for regular mail.

Now, I can do stuff like setting up a log viewer to send email when there's something important in one of the logs.

Thanks for your responses.  Although I still don't fully understand what's going on, I guess I can mark this solved.

---

