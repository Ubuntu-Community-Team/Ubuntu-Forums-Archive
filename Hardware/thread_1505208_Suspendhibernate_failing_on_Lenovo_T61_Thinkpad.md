---
title: "Suspend/hibernate failing on Lenovo T61 Thinkpad"
date: 2010-06-08
forum: Hardware
---

### Post by fivebells on 2010-06-08
I'm running Lucid.  pm-suspend and pm-hibernate both result in only a partial shutdown of some kind.  The fan and drive stop, but the LCD display stays on, displaying the last image at the time of attempted shutdown.  And the crescent-moon "I'm sleeping" light flashes at a higher frequency than it usually does during shutdown, and goes on flashing indefinitely.  (Usually it stops flashing after shutdown is complete.)

Not sure what could have caused this.  The laptop hadn't taken any updates or had anything installed recently.  (I've updated to the latest Lucid packages since this problem, though.  Didn't fix it.)  Simultaneously, as far as I can tell, wireless seems to have failed, too.  I haven't looked into that, yet, because it's less of a hassle at the moment.  (I am tethering off my phone.)  But it may be related.

I'd appreciate some suggestions on how to debug this.  There doesn't seem to be anything relevant in /var/log/{messages,debug,dmesg}.  /var/log/pm-suspend.log ends with a series of happy messages about each hook script running successfully, then says "performing suspend", then nothing else.

---

### Post by fivebells on 2010-06-10
A reinstall fixed this.

---

### Post by kkfok1 on 2010-06-11
I am also interested to know about this. I have just upgraded from Hardy to Lucid, the hibernate mode is working under Hardy after much research, and I hope not on Lucid again.

Basically after hibernate, it does not back to the previous state, instead it start from the beginning, this should be the shutdown function and not hibernate.

---

### Post by fivebells on 2010-06-11
Seems likely that you have a different issue, as a reinstall restored all functionality in my case.  Also, I suspect this thread won't get much attention now that it's been marked as solved.  You might want to start a new thread on the topic.

---

### Post by matthewglen on 2010-07-28
I'm having the exact same problem. I'm using a T61 (M/N 7662CTO), and have run Linux on it for about two years. I didn't used to have a problem with suspend/hibernate, but sometime in the past year (I'm tempted to say it was with the release of 9.10), the problem came up. I tried the fix given in [this thread]("http://ubuntuforums.org/showthread.php?t=690933"), but it didn't solve the problem. As far as I can tell, nothing is happening different.

I would be grateful for suggestions or simply links to relevant threads.

---

### Post by Misiunio on 2010-08-27
Blinking moon syndrome is most probably caused by some external **mounted** storage device. In my case this was sd card in build-in reader - removal of card solved suspend problem.

---

### Post by apos on 2010-09-29
I have this in

```
nano /etc/pm/config.d/00sleep_module
```

```
SUSPEND_MODULES="$SUSPEND_MODULES iwl3945 usb_storage sdhci sdhci_pci"
```

(Thinkpad T61 with Nvidia quadro nvs 140S)

The "iwl3945" reloads the wlan card.
"sdhci usb_storage sdhci_pci" assures that the card reader is reloaded.

Probably it helps ;)

---

### Post by euloiix on 2011-03-17
> **fivebells said:**
> A reinstall fixed this.

Hi fivebells, 

If you still follow the thread, could you explain what you did reinstall exactly ? And how ?

Thank you :D

---

