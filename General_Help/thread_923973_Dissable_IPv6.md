---
title: "Dissable IPv6"
date: 2008-09-19
forum: General Help
---

### Post by M4rotku on 2008-09-19
Hello all,

Now that I am in college, I have to connect to the internet via a sign-in page.  Well, since I am not using windows as most students, I am able to bypass the sign-in page and go directly to browsing.

However, when i tried to connect using a different Ethernet port or the wireless in my dorm, I am unable to.  I went to the IT guys here and they told me that it is because the IPv6 thing messes up their sign-in system and it has to be disabled.  They disabled it for me in Vista, but they do not support linux.  Fortunately, one of the IT guys uses another distro and told me that it would be somewhere in my Network options.

So, I opened the Network Tools menu and in the Devices tab, found some reference to IPv6 and IPv4.  However, I cannot find out how to change the settings, when I click the Configure button, it tells me:
> The interface does not exist
Check that it is correctly typed and
supported by the system.

Two questions,
1)  Do I need to disable IPv6 and possibly even IPv4 in order for this to work?
2)  How do I do this?

---

### Post by mb_webguy on 2008-09-19
I don't know why having IPv6 enabled on your system would have any effect on their sign-in system, but [this]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html") should help you disable it.

---

### Post by ju2wheels on 2008-09-19
Why do I have a feeling that their solution to forcing you log in to the network is IE/Windows specific?

The fact that IPv6, as the last poster stated would actually affect it doesnt make sense to me. From a network throughput standpoint, I believe IPv6 is much faster due to jumbograms, so if anything I would bet they want you to disable it so they dont have to worry about students saturating the network with their downloads (from university to uversity as those are the ones who typically have IPv6 backbones with blazing speeds).

I would go back and ask for another explanation.... hell tell him you disabled IPv6 and you are still getting the same results and see if they change their story lol.

---

### Post by mb_webguy on 2008-09-19
My question is what their sign-in page is for, and why you should be able to "bypass" it just because you're using Linux.

A lot of the time when I see university network sign-in pages, it's  because they're using MAC filtering, and the sign-in is a one-time only thing to add your MAC address to their database.  If this is the case, you can't bypass it, because no matter what OS you're using, your MAC address is the same, and you won't be allowed on the network unless your MAC address is in the system.

Find out exactly what kind of sign-in this is.  You might also try installing IE under Wine (I'd suggest using IEs4Linux) and seeing if it's simply that they use some sort of ActiveX control for the login.

Also, the next time you talk to the IT guys, ask what you'd need to do if you were using a Mac.  The solution should be fairly similar for Linux.

---

### Post by Nepherte on 2008-09-19
In Belgium every university has their sign in page to authenticate yourself. You sign in with a student number and a password so only students and university employees can access the network and through their network, the internet (I assume this is the case here). If you have to do it all the time it's not for the MAC address, but rather for bandwith limitations and of course, the authentication. MAC filtering has more sense in wireless networks. I don't believe it's a 'Windows only' thing either. If it's going through the internet/network, every thing with a tcp/ip stack will mostly suffice if you don't need an extra program. And last, IPv6 can mess up things if that network is not IPv6 compatible.

To see if ipv6 is enabled on your computer:
```
ip a | grep inet6
```
If there's an output, it is still active. This command should do the trick to disable it:
```
sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases
```
(It will then be disabled on rebooting).

---

### Post by M4rotku on 2008-09-19
Yes, that was the case, the university only wants to let students and faculty on.  I disabled it and now I am rebooting.

---

