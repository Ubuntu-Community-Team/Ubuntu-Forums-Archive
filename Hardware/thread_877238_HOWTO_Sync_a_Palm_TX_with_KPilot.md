---
title: "HOWTO: Sync a Palm TX with KPilot"
date: 2008-08-01
forum: Hardware
---

### Post by grokouser on 2008-08-01
If you have a Palm TX and want to use Kolab, you will want to sync using KPilot because this is how to sync calendar and contacts with Kontact. Kontact is a supported way to interact with the the free Kolab groupware server suite. I am posting this because the Palm TX does not seem to work "out of the box" with KPilot in Ubuntu 8.04 hardy. This is the simple procedure I followed to get it to work.

Be sure you have the Ubuntu packages kpilot and kontact. If you want to install Kolab server, select the package called kolabd. Only put Kolab server on a desktop that you leave on and connected to the internet all the time.

From the Palm's HotSync screen change the settings to "Local" and "Cradle/Cable".  On the same screen, select "Edit Connections".  Edit "Cradle/Cable" and choose "Edit" and then "Details". Set the speed to 19200 and set "Flow Ctl" to Automatic.

Then in KPilot use the dialog setup for Kpilot instead of the wizard. Set the speed to match "19200". The speed settings are set slower to enable a successful sync.

In the KPilot HotSync you may see the message "HotSync is disabled because KPilot could not determine the state of the screen saver".  In KPilot, go to Settings->Configure Kpilot->HotSync.  Uncheck the box "Do not sync when screensaver is active".

After this, I was able to sync my Palm TX with KPilot. Open Kontact to see a very nice Palm Desktop like view of the contents of your Palm TX! Good luck and I hope this posting was helpful.

---

### Post by davekenny on 2008-08-16
it also possible to use Kpilot and wifi.
install 'multisync'. use synapic..
for device use 'net:any'
kpilot with complain that it doesn't know what this device is.
run hotsync in Kpilot when it asks press the hot sync on the palm.
make sure the wifi on the palm is on and the network hotsync is selected. also the proper computer.

i've done it several times and it works :):):)

-Davekenny

---

