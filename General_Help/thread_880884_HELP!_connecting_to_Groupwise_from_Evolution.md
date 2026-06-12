---
title: "HELP! connecting to Groupwise from Evolution"
date: 2008-08-05
forum: General Help
---

### Post by jmghist on 2008-08-05
I am trying to connect Evolution to my Groupwise account. I have successfully tied into my hotmail/msn, but the Groupwise just won't work. I selected Novell Groupwise as my Server Type and then under Server: I entered the URL that I use to connect to Groupwise through my browser 156.111.111.16/gw/webacc (not the real address). When I try to connect, I get Error while Scanning folders in "GroupWise server mail.156.111.111.16/gw/webacc". Host lookup failed: mail.156.111.111.16/gw/webacc:Name or service not known.

I know my Groupwise account works because I can access it through the URL on my browser.

Any suggestions?

---

### Post by dcstar on 2008-08-06
> **jmghist said:**
> I am trying to connect Evolution to my Groupwise account. I have successfully tied into my hotmail/msn, but the Groupwise just won't work. I selected Novell Groupwise as my Server Type and then under Server: I entered the URL that I use to connect to Groupwise through my browser 156.111.111.16/gw/webacc (not the real address). When I try to connect, I get Error while Scanning folders in "GroupWise server mail.156.111.111.16/gw/webacc". Host lookup failed: mail.156.111.111.16/gw/webacc:Name or service not known.

I know my Groupwise account works because I can access it through the URL on my browser.

Any suggestions?

AFAIK the Evolution GroupWise access is for native GroupWise connections, not Web connections.

Evolution accesses Microsoft Exchange via a web interface, but not GroupWise - you probably need to find out from you IT people if the direct GroupWise port is available externally, if not then you cannot use it.

---

### Post by adrighem on 2009-07-30
Evolution uses SOAP to connect to the groupwise server. This is also used for the Groupwise Mobile service.

You just need to enter the server DNS or IP and ask which port is available as the SOAP port.

I can tell you that once you've configured that, it works like a charm, at least with 2.26. With older versions your mileage may vary.

---

### Post by ncweber on 2009-08-17
I'm trying to connect to my company's GroupWise server.  The administrator even opened the SOAP port for me.  However, no matter what I do, I cannot connect.  Either nothing happens at all, or I get an Authentication Failed error message depending on whether I include the mail server's port number in the server address line or not.  The mail admin is looking into it too, but seems to be as baffled as I as to why i cannot connect.

UPDATE: Nevermind, folks.  Both my admin and I forgot about opening the SOAP port in the company firewall. :P

---

### Post by decoherence on 2009-08-17
here are some screendumps of my working configuration.... nothing too interesting but sometimes a picture is worth a thousand words. obviously the hostname and port apply to my setup but maybe it'll give you an idea.

---

### Post by dr0i on 2011-07-21
I got the same disturbing authentication failure (while I knew my password is correct). The Cause was that I provided not only the port number for SOAP but the whole adress (with ip). So, just put in the portnumber and everything's fine. :)

---

