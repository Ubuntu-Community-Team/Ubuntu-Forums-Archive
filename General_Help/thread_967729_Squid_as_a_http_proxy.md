---
title: "Squid as a http proxy"
date: 2008-11-02
forum: General Help
---

### Post by mowbray on 2008-11-02
Hi

I have installed squid on my ubuntu 7.04 and using apt-get and configured it to allow  my internal network address range.

If I point the browser on the ubuntu box to itself as the proxy, I can browse the web and the proxy works OK. However, if I point any other client at the proxy then I can see a connection is made (by running netstat), however a page is never returned to the browser.

I am kind of suspecting that a proxy loop is taking place, but I dont know enough about squid or Linux to solve it.

Can anyone help? Have out missed out some crucial step?

I dont really want to make it a transparent proxy at the moment - I may come back to it later.

Thanks in advance.

Setup:

ADSL Wireless Router/Switch

Ubuntu 7.04 with squid installed

client on windows machine with proxy manually configured

---

### Post by mowbray on 2008-11-02
Forgot to add that the ubuntu box is configured with a single nic (it has two but only one is in use).

---

### Post by jona7han on 2008-11-02
Does your browser display a Squid error page? Maybe you need to add the acl all (acl all src 0.0.0.0/0.0.0.0) and then add the line http_access allow all

---

### Post by mowbray on 2008-11-02
Thanks for the response

I dont get an error page in my browser - it never displays anything at all. However if I leave the proxy manually configured and stop the squid daemon then I get an error saying it cant talk to the proxy so I know it is connecting.

I will also try what you suggest

Ta

---

### Post by mowbray on 2008-11-02
Squid didnt like the all rule with 0.0.0.0 in it. But I did try changing the last rule to http_access allow all - it didnt help.

It is defintely connecting but just not returning anything to the client.

---

### Post by jona7han on 2008-11-02
try to add the acl all as the IP range on your network i.e: acl all src 192.168.1.0/24 you might also want to see if there is a line that reads http_access_deny_all and remove it. The other thing is, even if Squid is denying you access because of an acl, you should see a error page in your browser normally saying something like proxy access denied, do you have a firewall on and is it blocking your squid port, probably 3128?

---

### Post by mowbray on 2008-11-02
Thanks. But I already tried adding my specific network range and getting rid of the deny all.

The client is definitely connecting - I can see it in netstat on the ubuntu machine running the proxy server. It just never returns anything to the client.

The firewall is not the problem, otherwise the initial connection would fail (and I have tried turning it off).

---

### Post by mowbray on 2008-11-02
I have connected from a network client using telnet to port 3128 on my ubuntu squid box. I can then issue a http get command for google and it returns the raw html.

I am really confused - why doesnt this work in IE or Firefox??

---

### Post by mowbray on 2008-11-04
Is there any one who can offer me some advice on this?

Thanks

---

