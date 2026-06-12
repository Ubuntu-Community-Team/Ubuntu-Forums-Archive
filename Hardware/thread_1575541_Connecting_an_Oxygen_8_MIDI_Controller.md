---
title: "Connecting an Oxygen 8 MIDI Controller"
date: 2010-09-15
forum: Hardware
---

### Post by mattbrand on 2010-09-15
Hey all. I'm brand new to Ubuntu (and Linux really), so please excuse my ignorance.

I'm trying to connect my Oxygen8 MIDI keyboard in order to play and record through LMMS.

I have LMMS installed. I can see the Oxygen8 when I list the USB devices using 'lsusb'. I have JACK installed. In JACK, under Setup, I have the Oxygen8 selected for Input as 'hw:1'. In JACK, under Connections, I have the Oxygen8 as input connected to the Midi Through as output.

When I try to Start JACK, I get the following error:

> [COLOR=#999999]22:01:35.510 JACK was started with PID=1604.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]22:01:35.581 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]22:01:35.582 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:01:35.583 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]22:01:36.009 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]22:01:37.680 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
I added the two lines to limits.conf, and restarted JACK, and even restarted my computer, to no avail.

I also installed MidiSport, andtried the following:
sudo fxload -D /dev/bus/usb/006/005 -I MidiSportKS.ihx

And got this message:
"can't modify CPUCS: Broken pipe"

Anyone have any advice?

---

