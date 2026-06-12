---
title: "Problems with iwpriv"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by coderasm on 2005-11-29
Hello, I'm trying to enable my internet access under WEP encryption.  I'm having trouble with the commands to enable WEP access.  I was told to use

sudo ifconfig eth1 down
sudo iwpriv eth1 authmode 2
sudo ifconfig eth1 up

I understand that I'm bringing down the interface, resetting privilages and then bringing it back up again.  My problem lies with the iwpriv command. When I run the command as written above, my output is 

authmode is not a valid command

when I run iwpriv by itself, the only options I see are

philip@ubuntu:~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

eth1      Available private ioctls :
          set_power        (8BE0) : set   1 int   & get   0
          get_power        (8BE1) : set   0       & get  80 char
          set_mode         (8BE2) : set   1 int   & get   0
          get_mode         (8BE3) : set   0       & get  80 char
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get  16 char
          reset            (8BE6) : set   0 int   & get   0
          sw_reset         (8BE7) : set   0 int   & get   0
          monitor          (8BE8) : set   2 int   & get   0

sit0      no private ioctls.

Here, eth1 is my wireless adapter.  I see no authmode ioctrl.  How do I make the authmode ctrl available for changing?  Thankyou

---

### Post by Lambert on 2005-11-29
iwpriv is driver specific. It depends on the drivers coding on what commands you have with iwpriv.

when you run just iwpriv, this is how you get what choices you have. So with your output it doesn't look like there are options to change wep mode via iwpriv.

More then likely it's not necessary as why you don't have that.

By the way, the command you're using authmode I believe is an atheros chipset/madwifi specific command which changes wep from open to shared key format.

So if you're trying to enable wep post the following.

1. open or shared system
2. hexadecimal or ascii key format
3. device and model number you're using for wireless
4. What driver you're using
5. output of your /etc/network/interfaces file (keep format but xxx our private data)

---

