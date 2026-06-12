---
title: "Karmic XNest problem"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Ravenheart on 2009-11-03
I have just upgrade to Karmic from Jaunty and I have a small problem.  When I went to use XNest there was no entry in the System Tools menu. I searched all the other menus and there was no sign of it at all. I have uninstalled and reinstalled it via synaptic but alas no joy.  I have even installed Xephyr but no joy there either, no sign of it in the Application menus either. I am a bit of a noob - Am I doing something totally obvious wrong? All help accepted.

---

### Post by pbrito81 on 2009-11-18
Hello!

Apparently Xnest has become obsolete and was removed from Karmic. Now you have to use Xephyr.

$ Xephyr :1

Unfortunely, this command just create a empty window... I don't know how to start a gnome session in there, sorry.

---

### Post by Ravenheart on 2009-11-19
Thanks for the reply.  I was starting to give up hope.  I too got a black window and some error messages in the terminal.  I just have to do a bit more research I guess.:confused:

---

### Post by rcorbish on 2010-01-12
Ignore the error messages - they don't seem to affect things working

**Xephyr -ac -query <my-remote-machine> :1 -screen 1024x768 -br 2>/dev/null  &**

Works OK for me - better than Xnest anyway

---

### Post by Ravenheart on 2010-01-18
Thanks for the post.  However I still get a black window using the above command.  I believe that the -query flag is querying the hostname for a remote login seission i.e. GDM.  Having read the Gnome help it appears that XDMCP is turned off by default.  A quick google search and I am led to believe that the easiest way to turn it on is to turn on remote desktop access. Did that and still just a black window that swallows my mouse pointer like the Black Hole of Death ;-).Remote Desktop access works though.  Truely stumped!!

---

### Post by rcorbish on 2010-01-19
edit **/etc/gdm/custom.conf**

in the **[xdmcp]** section ...

[B][xdmcp]
Enable=True
DisplaysPerHost=2
[/B]


Then reboot the server.

Only do this if you're behind a firewall !

---

### Post by Ravenheart on 2010-01-20
:DExcellent!! It works just like it used to. Many thanks.

---

### Post by coollinn on 2010-02-23
I can't found the [xdmcp] section in the /etc/gdm/custom.conf. 
Added this section to custom.conf file, then reboot system,but the problem still.  I can't remote login to solaris used by xnest which display black blank yet.  

Please give me some advice. 

My /etc/gdm/custom.conf: 
laptop:/etc/gdm$ more custom.conf 
:confused:
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=chenlin
AutomaticLogin=chenlin
TimedLoginDelay=30


[I]edit /etc/gdm/custom.conf

in the [xdmcp] section ...

[xdmcp]
Enable=True
DisplaysPerHost=2

Then reboot the server.
Only do this if you're behind a firewall ![/I]

---

