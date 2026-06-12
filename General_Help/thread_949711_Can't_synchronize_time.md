---
title: "Can't synchronize time"
date: 2008-10-16
forum: General Help
---

### Post by emakarov on 2008-10-16
Hello,

I set the time preferences to synchronize with ntp.ubuntu.com. I have ntpd and ntpdate installed. However, the clock is not synchronized (it's about 1 minute off).

From [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) I see that one problem is that "ntptrace ntp.ubuntu.com" prints

europium.canonical.com: timed out, nothing received
***Request timed out

That page also mentions DHCP issues but unfortunately I don't know enough to know if there is a problem with that.

When I try "sudo ntpdate ntp.ubuntu.com" I get

16 Oct 13:28:34 ntpdate[11346]: the NTP socket is in use, exiting

Another issue is that synchronization probably can't take place at startup because at that time I do not have Internet connection yet. I have to manually run VPN client to connect to my school WiFi network.

Is it possible for NTP daemon to synchronize when the network connection becomes available?

Thank you,
Evgeny

---

### Post by HalPomeranz on 2008-10-17
The "the NTP socket is in use, exiting" error message is because you're trying to run ntpdate while the NTP server is running.  Try this:

[CODE]
sudo /etc/init.d/ntp stop
sudo ntpdate ntp.ubuntu.com
sudo /etc/init.d/ntp start
[CODE]

If ntp.ubuntu.com is not responding, try pool.ntp.org instead.

---

### Post by emakarov on 2008-10-17
"udo /etc/init.d/ntp stop" seemed to work OK (printed "* Stopping NTP server ntpd [ OK ]") but both "sudo ntpdate ntp.ubuntu.com" and "sudo ntpdate pool.ntp.org" print

17 Oct 13:49:45 ntpdate[8487]: no server suitable for synchronization found

Evgeny

---

### Post by HalPomeranz on 2008-10-17
It sounds like you're unable to contact other NTP servers for some reason.  I assume that you're posting to these forums from the machine that you're trying to use NTP on, so your network connection is working properly at least as far as reaching other Internet sites via HTTP.

Could there be some sort of firewall in the way that's stopping your NTP traffic?

---

### Post by emakarov on 2008-10-20
Yes, it turned out that the university network blocked some traffic. I was able to synchronize with a university server, though.

Evgeny

---

