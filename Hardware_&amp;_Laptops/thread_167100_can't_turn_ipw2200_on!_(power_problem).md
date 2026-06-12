---
title: "can't turn ipw2200 on! (power problem?)"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by sliorda on 2006-04-27
Just installed 5.10 and after following [http://ubuntuforums.org/showthread.php?t=13576]("http://ubuntuforums.org/showthread.php?t=13576") I still can't power up my ipw2200 card. I have ThinkPad 50e.

Under windows an antenna LED is turned on when the wifi is enabled. I think it an indicator to the state of power supply to the card. How can I turn it on?

```

root@ibmlappy83:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth2      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

BTW: what's "sit0" ?

Thanks.

---

### Post by basketcase on 2006-04-27
it seems to be an issue with Ubuntu (linux?).  Also I don't believe it is an issue with 'power' but an issue with the LED itself.  The card works, but no LED on the front.  

When I initially installed 5.04 everything worked.  Went to 5.10 and wifi was something that didn't work.  

I'm hoping it will get fixed with Dapper.  I'm downloading the Release 2 ISO now to see if it gets fixed.

---

### Post by basketcase on 2006-04-27
btw, if you haven't already you might want to check out

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by sliorda on 2006-04-27
when the card is turned off from windows and i'm booting into linux, the card is unusable and the led is off. when i'm logging off windows while the card is on (as the led), and boot into linux, the card is working and the led is on.

it seems like a power control problem in linux.

or maybe it's a thinkpad issue?

thanks.

---

### Post by basketcase on 2006-04-28
[QUOTE=sliorda]when the card is turned off from windows and i'm booting into linux, the card is unusable and the led is off. when i'm logging off windows while the card is on (as the led), and boot into linux, the card is working and the led is on.

it seems like a power control problem in linux.

or maybe it's a thinkpad issue?

thanks.[/QUOTE]
Here is what I learned tonight testing with my Notebook.  

Dapper 6.06 RC 2 (latest beta whatever it is).  

Still no LED...but, there is a nifty little wifi notification thing, and I used the wifi to install all the updates while it was installing, so it does work.  

Upon initial boot up, it said 'active' but 'disconnected'.  On my Dell it is an FN + F2 and that turns the radio on.  As soon as I had done that, BAM....I was connected.  

I'm replying to this message on my notebook via Wifi OUT OF THE BOX with Dapper.  

If there is anything you'd like to know let me know.

---

