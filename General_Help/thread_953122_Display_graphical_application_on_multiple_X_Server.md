---
title: "Display graphical application on multiple X Servers"
date: 2008-10-19
forum: General Help
---

### Post by rampageoberon on 2008-10-19
Hi,

I am looking a tool/method which will allow me to view a graphical application on multiple X servers simultaneously.

Example: have Pidgin running on my desktop, and then access the same pidgin session without having to VNC in and view the full desktop.

I came across this page [http://www.faqs.org/faqs/x-faq/part6/section-4.html](http://www.faqs.org/faqs/x-faq/part6/section-4.html) and toos such as XMX and xmove but can not work out how to use them to do what I want. (Kept getting "file not found" errors trying to execute XMX)

Anybody done this before, or is able to point me in the right direction with this.

Thanks

---

### Post by ghost_ryder35 on 2008-10-19
ssh with Xforwarding

---

### Post by rampageoberon on 2008-10-20
Thanks for the reply. I don't want to start a new instance of the application, I want to view the already running instance.

Not sure SSH and X11Forwarding allows me to view an already running instance. If there is a way please tell how?

---

### Post by ghost_ryder35 on 2008-10-21
well... i'll keep looking but you could do the pidgin thing on the cli.  FINCH is a cli version of pidgin, so if pidgin is setup on your box then FINCH will work.  If you use SCREEN you can detach and attach all day long....  Check it out if you dont mind the CLI
```

ssh yourbox.com
sudo apt-get install finch
screen
finch

```
Then close the terminal it is in by hitting the x button on the menu bar
then
```

ssh yourbox.com
screen -r

```

---

