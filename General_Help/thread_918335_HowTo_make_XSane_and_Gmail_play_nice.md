---
title: "HowTo: make XSane and Gmail play nice"
date: 2008-09-12
forum: General Help
---

### Post by flabdablet on 2008-09-12
XSane has a scan-to-email facility that knows how to talk to an SMTP server.  Gmail uses an SMTP server that requires a secure (SSL) connection.  XSane's SMTP support doesn't do SSL.  I didn't want to install and configure a full-blown MTA like Postfix or Exim just to make these things work together.  Here's what I did instead.

First thing is to make sure the necessary packages are installed:
```
sudo apt-get install openssl xinetd

```
Next, create a little wrapper to talk to the Gmail SMTP server without injecting extra text we don't want:
```
sudo tee /usr/bin/gmail-smtp <<EOF >/dev/null
#!/bin/sh
/usr/bin/openssl s_client -connect smtp.gmail.com:465 -quiet 2>/dev/null
EOF
sudo chmod +x /usr/bin/gmail-smtp

```
Test the connection:
```
gmail-smtp

```
After a short delay, you should see something like
**220 mx.google.com ESMTP f42sm17489123rvb.6**
If you then type
**helo**
you should get something like
**250 mx.google.com at your service**
and typing
**quit**
should get you
**221 2.0.0 mx.google.com closing connection f42sm17489123rvb.6**
and your shell prompt back.

Now we need to make that wrapper available as a local network service, so XSane can use it:
```
sudo tee /etc/xinetd.d/gmail-smtp <<EOF >/dev/null
# default: on
# description: Gmail SMTP wrapper for clients without SSL support
service gmail-smtp
{
    disable         = no
    bind            = localhost
    port            = 10025
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/bin/gmail-smtp
    type            = unlisted
}
EOF
sudo /etc/init.d/xinetd reload

```
The output of
```
netstat -ltn

```
should now include a line that looks like this:
**tcp 0 0 127.0.0.1:10025 0.0.0.0:* LISTEN**
and
```
telnet localhost 10025

```
should get you a conversation with Gmail's SMTP server like the one you had above.

All that remains is to configure XSane.  Under the Email tab in the Setup menu, set the SMTP server address to localhost, the port to 10025, fill in your Gmail account details, and select ASMTP Login authorization.

I'm subscribed to this thread in case you have trouble.  Enjoy!

---

### Post by FedeGhigo on 2009-08-26
A fantastic & easy guide ! Thank you very much.

---

### Post by toasted124 on 2009-11-04
Thank-you so much for publishing this guide and sharing this information!!!!!! I used it to create a connection to yahoo mail as well. 

I followed the procedure exactly, replacing gmail-smtp with yahoo-smtp and it works!

Xsane now is able to send scanned images to recipients via SSL on yahoo mail.

---

### Post by p1mpn8nt3z on 2010-08-12
[B]Extremely well written, concise and helpful! 
Thank you very much for your help, and btw: that was SO phat how you figured out that the underlying problem was SSL[/B]-

[B]For Me: Another giant step away from Winblows\\:D/
For You: Beers on me if ever we perchance should meet![/B]

---

### Post by fcorades on 2010-08-21
Great work!!! Thank you.

In my server openssl go to 100% cpu, to avoid this i suggest to change (**/usr/bin/gmail-smtp**):

[I]#!/bin/sh
/usr/bin/killgmail&
/usr/bin/openssl s_client -connect smtp.gmail.com:465 -quiet 2>/dev/null[/I]

and create the file (**/usr/bin/killgmail**) :

[I]#!/bin/sh
sleep 10
killall openssl[/I]

and then make it exec:

**chmod +x /usr/bin/killgmail ** 

With this mod openssl is terminated after 10 sec ... is enough to send 1 mail.
Of course this solution is a bad idea if you have concurrent openssl sessions.

---

### Post by High Roller on 2010-08-21
> **fcorades said:**
> Great work!!! Thank you.

In my server openssl go to 100% cpu, to avoid this i suggest to change 

I have the same problem.
I guess the more important question would be why is it doing this?  Seems like some kind of bug.

---

### Post by flabdablet on 2010-08-22
I have not seen this behavior, so I can't help much with the bug. But I'd like to offer the following alternative workaround, which is a little less convoluted and avoids using "killall" (I've never been a fan of risking the death of more processes than necessary).

Replace the gmail-smtp script creation step from my original post with this:
```
sudo tee /usr/bin/gmail-smtp <<EOF >/dev/null
#!/bin/sh
exec 3>&0
/usr/bin/openssl s_client -connect smtp.gmail.com:465 -quiet 2>/dev/null 0<&3 &
sleep 10
kill $! 2>/dev/null
EOF
sudo chmod +x /usr/bin/gmail-smtp
```
In the initial testing stages you might want to replace the "sleep 10" with something more generous.

---

### Post by High Roller on 2010-08-24
> **flabdablet said:**
> Replace the gmail-smtp script creation step from my original post with this:


Your alternative doesn't appear to function for some reason.
This bug is occurring on 3 separate computers that I have.
Openssl continues to run at 100% and more instances spawn each time an e-mail is sent.
I can only see the process running under the "top" command and not under "System"-->"Administration"-->"System Monitor"-->"Processes(tab)".

And yes, I feel icky using "killall".

---

### Post by flabdablet on 2010-08-24
Weird.

What happens if you exercise gmail-smtp directly, and what happens via telnet?

---

### Post by High Roller on 2010-08-25
> **flabdablet said:**
> Weird.

What happens if you exercise gmail-smtp directly, and what happens via telnet?

When I use gmail-smtp as described in your how-to the "openssl" process ends after I type "quit".

When I use telnet as described in your how-to the "openssl" process remains active even after telnet has been closed.

---

### Post by flabdablet on 2010-08-25
Could be an xinetd bug then.

Since writing this howto I've jumped ship from Ubuntu, but I've just this minute tested it all again in Debian Squeeze and it all still works fine for me. If you figure out what's breaking it for you, I'd be interested to hear about it.

---

### Post by flabdablet on 2010-08-25
Just out of interest: what output do you get from the following commands?```
openssl version
sudo xinetd -version
```On Squeeze, I'm currently seeing```
stephen@jellyfish:~$ openssl version
OpenSSL 0.9.8o 01 Jun 2010
stephen@jellyfish:~$ sudo xinetd -version
xinetd Version 2.3.14 libwrap loadavg
stephen@jellyfish:~$ 
```

---

### Post by High Roller on 2010-08-26
> **flabdablet said:**
> Just out of interest: what output do you get from the following commands?```
openssl version
sudo xinetd -version
```


I get the following:
```
OpenSSL 0.9.8k 25 Mar 2009
xinetd Version 2.3.14 libwrap loadavg
```

---

### Post by abandonow on 2010-10-20
After I upgraded to 10.10 (not 100% sure) the OpenSSL process is using 100% cpu at boot.

```
root      1638 97.5  0.0   4296  2012 ?        R    14:44   4:20 /usr/bin/openssl s_client -connect smtp.gmail.com 465 -quiet
```

Any tips?

---

### Post by flabdablet on 2010-10-20
abandonow, what does ```
openssl version
``` show for you?

If Ubuntu is still using something earlier than the 0.9.8o version that's currently working fine for me in Debian Squeeze, you might want to try installing a more up to date [COLOR="Blue"]_[Debian package]("http://packages.debian.org/squeeze/openssl")_[/COLOR] into your Ubuntu. Just download the .deb and install it with gdebi or dpkg -i; if it breaks things, uninstalling and reinstalling openssl using synaptic or aptitude should get you your original Ubuntu version back.

---

### Post by DaveWard on 2010-11-01
I had the problem and it was related to openssl hanging due to a lack of entropy on the system causing openssl to block while waiting for more to be generated. There was no particularly obvious reason it used 100% cpu while doing it though! 

You can check available entropy by cat'ing /proc/sys/kernel/random/entropy_avail (which will itself use some entropy due to the way cat will is spawned so don't do it often - in a script for example; if you want to monitor it use somehting else like munin for example). if you have < 150 bytes of entropy all the time its likely openssl will be blocking.

You can use audio entropy video entropy and timer entropy daemons (google them) to generate more entropy on a system or use the elegant hardware solution from simtec [http://www.entropykey.co.uk/](http://www.entropykey.co.uk/). 

Hope this helps!

---

### Post by flabdablet on 2010-11-02
Something else people experiencing the hang problem might care to try is including the **-bugs** and/or **-no_ticket** options in the **openssl s_client** command line inside /usr/bin/gmail-smtp. I don't know if these will make any difference but I have seen a couple of other ssl hangs talked about in various fora where they did. For what it's worth, gmail-smtp works fine for me both with and without these options.

---

### Post by tigner on 2012-05-08
Hi,


I have this mostly working under FreeBSD, yeah, I know it is not ubuntu, or even linux.


I want to scan documents and email to my msu email account. I created a version of
the program and setup the inet server correctly. I have added the wrapper to the inet.conf
and /etc/services files so that when I type "telnet localhost 10025" I get connected to the
campus email server .I have entered my correct email info into xsane/setup and when I try to send a scanned doc, I get a response from the server "ASMTP authentication failed". 


The file I created is /usr/local/bin/msu-smtp, it is executable and has the following lines.
#!/bin/sh
openssl s_client  -connect mail.msu.edu:465 -quiet 2>/dev/null



I can manually connect using the base64 version of my username and password to get into the
mail server and send myself an email message.


When I try the same thing in xsane, I get the "ASMTP authentication failed" message.


I use the same username and password.


Do you have any suggestions ?


Thank you,


Barry

---

### Post by flabdablet on 2012-05-08
If that were my system, I'd try the following:

1. Try both "ASMTP Plain" and "ASMTP Login" options in XSane's setup window. I would not expect to have to base64-encode the credentials I gave to XSane; I would expect XSane itself to do that if necessary.

2. Modify msu-smtp so it logs all input and all output using something like
```
log=/tmp/msu-smtp-$$.log
tee -a $log | openssl s_client -connect mail.msu.edu:465 -quiet 2>/dev/null | tee -a $log
```
and look for differences between what XSane is doing and what works by hand.

3. Set up a proper mail client (Thunderbird?) to connect successfully to my email account, then modify its settings to make it go via localhost:10025 with no encryption rather than going directly to mail.msu.edu:465 with encryption; verify that it can still send mails; then look for differences between what gets logged for it and what gets logged for XSane.

If it turned out not to be possible to make XSane handle the auth procedure required by the mail server, I'd figure out how to make msu-smtp munge the auth stuff on the way through, perhaps to the extent of having msu-smtp handle it fully internally so that XSane could just use plain SMTP.

I'd be interested to hear how you get on.

---

### Post by lisati on 2012-05-09
Thread closed, necromancy.

---

