---
title: "Fn-F2 key combination not working  with Dell Inspiron 9400"
date: 2009-06-18
forum: Hardware
---

### Post by pagheca on 2009-06-18
Hi,

I have Ubuntu 9.04 installed on a Dell Inspiron 9400, dual boot with WinXP. 
When running XP I can turn on and off the internal wireless card by toggling the key combination Fn-F2, as expected. I can also do it when running Ubuntu, but *only* if my card was ON at bootstrap. 

This is quite an inconvenience because if I bootstrap Ubuntu with the card off and need to connect to a wireless network, I have to shutdown, boot on WinxXP, switch on the internal wireless card, shutdown again, and boot Ubuntu again. 

Note that, if I bootstrap on Ubuntu, and the wireless is ON, I can switch it off and on again. 
Does anyone knows about this little but annoying problem?

thanks,
pagheca

---

### Post by sdennie on 2009-06-18
Contrast the difference the following command when the card is working and when it's not working.  If you don't get any output when it's not working but do when it is working, you may be able to solve your problem just by manually loading the drivers at startup.

```

lsmod | grep iwl

```

This will only work if you have intel wireless.  If you have some other type of wireless, you'll need to post the output of:

```

lspci
lsmod

```

---

### Post by pagheca on 2009-06-19
First, many thanks for the help.

I didn't notice any change in the output of 

[FONT=Courier New]$ lsmod | grep iwl
iwl3945                97912  0 
mac80211              217208  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
[/FONT]
As you can see the card is an intel. Actually I found that sometime (not always) it takes some time for the card to switch on after it has been switched off (up to 5 seconds), while other times it switches on immediately.

I'm trying to understand if is just this "laziness" in the card at the origin of the problem aka I haven't waited long enough... 

Thanks,
pagheca

---

