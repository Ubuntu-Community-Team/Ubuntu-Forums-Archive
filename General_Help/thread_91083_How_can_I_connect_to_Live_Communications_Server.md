---
title: "How can I connect to Live Communications Server?"
date: 2005-11-16
forum: General Help
---

### Post by dguy on 2005-11-16
Hi everyone, I just recently switch from Windows, and it's been great so far. My first big issue is that my work office is still mainly a Windows-based LAN, including Exchange for email/groupware and Live Communications Server for internal IM. For mail I can use Web Outlook or Evolution so that's no problem, but I have not found anything that let's me communicate with my co-workers through Live Communications server. I've tried both Gaim and Kopete, but neither of them seem to support SIP messaging. If it were up to me, I would just set up a Jabber server, but for the time being, that isn't possible.
 
My co-workers and manager are pressuring me to find a solution quick or drop Linux and go back to Windows... I would hate to have to return to Windows because Linux has no SIP client that would let me connect to Live Communications Server, but sadly, I may have to.

Any suggestions?
 
Thanks in advance

---

### Post by rmjokers on 2005-11-16
I was searching for a similar answer a while back.  This discouraging article might shed some light on the issue: [http://www.messagingpipeline.com/trends/53700175]("http://www.messagingpipeline.com/trends/53700175")

---

### Post by dguy on 2005-12-08
Ah so MS uses proprietary extensions to SIP... and the only way to work with it is through their API that only works with Windows. I found out Trillian has a plug-in for this, but is obviously Windows-only software that uses this API. I thought it seemed strange that nobody had created some plug-in for an IM client that works under Linux. This sucks, I guess it's another reason to push for a Jabber server here in the office since we also have a couple people using mac OS X.

Actually, the main thing that people like using Windows Messenger for is application sharing. I think that's the last main reason they don't want to move to Jabber. Anyone know if application sharing is possible to do cross-platform? Would something like VNC work? Or is there a better solution?

---

### Post by blackmax on 2006-02-28
I'm in the same boat.  I work in a MS shop that uses LCS and I have migrated to Ubuntu on my laptop.  I’ve searched for an LCS SIP compatible Linux IM client, but have not had much luck.  

My current work around is to RDP from my Ubuntu desktop to one of the MS machines here in the office and then pull up MS Office Communicator on the remote machine and monitor it for messages.  

This is not a very eloquent solution, but it does allow me to run Ubuntu and chat via LCS at the same time.  Given the continued emergence of LCS in more and more businesses I'm guessing it is just a matter of time before someone (GAIM perhaps) writes a MS SIP compatible plug-in for their Linux IM client.

---

### Post by dguy on 2006-02-28
I have actually been able to set up an XMPP server (using [Wildfire]("http://www.jivesoftware.org/wildfire/") which is very nice by the way) here at our office and everything is working great, not everyone is using it yet. But so far it's working well, and it's *open*, so our mac users don't feel left out any more either. ;p

Although I'd like to see a linux client compatible with LCS, after reading the article rmjokers posted, I think that is unlikely. Microsoft's version of SIP uses proprietary extensions and they've made sure that the only way to develop clients to connect to LCS is by using their SDK, which of course is Windows-only. The only way this could happen is if someone were to to reverse-engineer the MS protocol, but I honestly don't think that LCS is widespread enough for that and I think XMPP is getting more popular as internal IM for businesses who need cross-platform compatibility.

---

### Post by blackmax on 2006-04-04
Our business just rolled out the MS Office Communicator web client for Live Communication Server.  Now I can use Ubuntu in the office and chat directly on the business Live Communication Server using Firefox.  Sweet!  :D

---

### Post by Jamie Jackson on 2007-08-22
Pidgin's got a [ plugin]("http://ubuntuforums.org/showpost.php?p=3235359&postcount=3") for it. No TLS yet, but it's next on the list.

---

### Post by steffen on 2008-04-22
Might try this?
[http://sipe.sourceforge.net/](http://sipe.sourceforge.net/)

---

### Post by Jamie Jackson on 2008-04-23
> **steffen said:**
> Might try this?
[http://sipe.sourceforge.net/](http://sipe.sourceforge.net/)

Nope, that's the plugin that I mentioned and it's not ripe yet. Judging from the [lack of progress]("http://developer.pidgin.im/ticket/48"), I doubt it ever will be.

---

### Post by steffen on 2008-04-24
...I see now that the lack of TLS prohibits me from using it in my company.

---

