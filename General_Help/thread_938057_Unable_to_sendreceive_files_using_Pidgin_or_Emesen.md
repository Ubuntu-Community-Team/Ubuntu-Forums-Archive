---
title: "Unable to send/receive files using Pidgin or Emesene"
date: 2008-10-04
forum: General Help
---

### Post by Aero-Z on 2008-10-04
Hello,

I have both Pidin and Emesene installed but I'm unable to send or receive files with them.
If somebody send a file to me using Emesene then I don't see anything. When I send a file to somebody else, the transfet won't start.
When sending file with Pidgin I see waiting for transfer to begin text but the other person sees that I cancelled the transfer.
My iptables is empty - no policies defined.

What might be the problem?

Thanks.

---

### Post by Aero-Z on 2008-10-04
Bump

---

### Post by Sef on 2008-10-04
Please don't bump until 24 hours have gone by.  Thank you.

---

### Post by Aero-Z on 2008-10-07
Bump

---

### Post by Lasering on 2009-09-02
Exactly my problem.
Can anyone help?

---

### Post by Vince N on 2009-09-02
Have any of you set up or configured any kind of firewall application?  Most times IM programs use different ports for that kind of thing and it may be blocked.

---

### Post by Lasering on 2009-09-02
> **Vince N said:**
> Have any of you set up or configured any kind of firewall application?No.

> **Vince N said:**
> Most times IM programs use different ports for that kind of thing and it may be blocked. How can I know what port does emesene uses to send files, and how can I know if it is blocked?

---

### Post by Vince N on 2009-09-02
It really depends on what protocol your using to send it.  For example AIM uses TCP and UDP ports 5190, Yahoo I think uses port 80, "which is kinda silly since thats the port a HTTP server might run on", and MSN uses a bunch of different ports.

Furthermore the issue may not even be with Ubuntu per say as your own hardware firewall in your modem, if it has one, may cause similar issues.

You could maybe install a firewall application, such as firestarter, and use it to monitor the incoming and outgoing connections to your PC and see what happens when you attempt to do a file transfer.  Past that I really don't know as I do not use File Transfer features of IM's much.

---

### Post by Lasering on 2009-09-04
My modem indeed has a hardware firewall which I disabled long time ago. Because if I enable it I can't access the internet.

I'll try firestarter and say something later.

---

