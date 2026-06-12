---
title: "CPU governer has to go back to ondemand after TLP"
date: 2013-05-22
forum: Hardware
---

### Post by user_of_gnomes on 2013-05-22
I experimented with TLP and a guide told me to disable the standard Ubuntu governer which I did.
However, I no longer want to work with TLP and would like to put the standard governer back in charge.

I can't figure out how to do it.

This was the result of my removing the standard governer, I copied it in case I would forget what I did. (Not that it helped)

```
 Removing any system startup links for /etc/init.d/ondemand ...
   /etc/rc2.d/S99ondemand
   /etc/rc3.d/S99ondemand
   /etc/rc4.d/S99ondemand
   /etc/rc5.d/S99ondemand
```

How do I put it back?

---

### Post by linrunner on 2013-05-22
Hi,

reenable it with:
```
sudo update-rc.d ondemand defaults
```
(from the [FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html#scaling"))

Would you mind telling why TLP did not meet your expectations?

---

### Post by user_of_gnomes on 2013-05-22
> **linrunner said:**
> Hi,

reenable it with:
```
sudo update-rc.d ondemand defaults
```
(from the [FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html#scaling"))

Would you mind telling why TLP did not meet your expectations?

Hello Linrunner, 

Thanks for taking the time to get back at me! 

I think TLP is actually pretty nifty but I need to see if my Radeon card can clock itself back* using as I need to implement this solution on another computer where switching power profiles is too much of a burden on the user.

*
```
#!/bin/sh
 
# ATI power save
echo dynpm > /sys/class/drm/card0/device/power_method

```

I will probably reinstall TLP as I like the idea of being in control of the power consumption of my desktop computer but from [what I understood, you can not use dynpm with TLP]("http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter").

---

### Post by user_of_gnomes on 2013-05-22
Funny thing; when I let the Ubuntu governer do the governing, the system boots very quickly. When I uncomment the related section in TLP (and deactivate the Ubuntu governer) it can take over 5 minutes before I can do anything, not even SysRQ REISUB responds during that time.

---

### Post by linrunner on 2013-05-23
> **UbuntuRaptor said:**
> what I understood, you can not use dynpm with TLP
Correct. At the time (around 2010) when i built radeon power save into TLP, dynpm was unusable on my hardware, so i left it out. I'll put it on my short list again.

> **UbuntuRaptor said:**
> Funny thing; when I let the Ubuntu governer do the governing, the system boots very quickly. When I uncomment the related section in TLP (and deactivate the Ubuntu governer) it can take over 5 minutes before I can do anything, not even SysRQ REISUB responds during that time.
Maybe TLP activates the governor too early. I'll look into that too. For the moment you should stick with the Ubuntu method.

Which governor did you use?

---

### Post by user_of_gnomes on 2013-05-24
> Correct. At the time (around 2010) when i built radeon power save into TLP, dynpm was unusable on my hardware, so i left it out. I'll put it on my short list again.

So far I have tried dynpm with a 5770 and it took it down 5 degrees Celcius whereas the lowest power profile takes it down 20 degrees C
I also tried dynpm on a passively cooled 5450 and it didn't make any difference. The lowest power profile only took it down 10 degrees C, though.

I don't think dynpm will make a very good addition in its current state.

> Maybe TLP activates the governor too early. I'll look into that too. For the moment you should stick with the Ubuntu method.

Which governor did you use? 

I used the ondemand for AC and powersave for bat.

However, I have a theory as to why it takes longer to boot up: Whenever I start tlp it starts in battery mode. Does it also cause your system to boot with the battery settings? That would explain why it'd take much longer to load.

On top of that, I have loaded ATI proprietary drivers and then switched back to the open-source radeon drivers. Something I only recently learnt is not a wise thing to do. My installation might not be a hundred percent any more. 

I now use the Gnome add-on to switch power profiles and I set the computer of the user that can't be bothered with profiles to "low" using the script I quoted earlier, doesn't seem to impact performance much under Unity. (It does under Gnome).

---

