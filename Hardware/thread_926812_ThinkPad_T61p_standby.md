---
title: "ThinkPad T61p standby"
date: 2008-09-22
forum: Hardware
---

### Post by xak on 2008-09-22
I am now on my second install of Hardy 8.04.1 on my ThinkPad T61p 6457-7WU, each suffering from the same Standby / Suspend issue.  I have followed these howto's:

[LIST]
[*][Nabble - Linux Thinkpad - HowTo make stable suspend and even hibernate on ThinkPad T61 with Ubuntu Hardy Heron]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Hardy_Heron_on_a_T61p#Suspend")
[*][Install Ubuntu Hardy Heron on a T61p - ThinkWiki]("http://www.nabble.com/HowTo-make-stable-suspend-and-even-hibernate-on-ThinkPad-T61-with-Ubuntu-Hardy-Heron...-td17618595.html")
[/LIST]

and used Envy to install nVidia driver 173.14.12 for the Quadro FX 570M, and modified **/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-lenovo.fdi** and have tried both of the following quirks:

```

     <match key="system.hardware.product" prefix_outof="6457;6460">
	<merge key="power_management.quirk.s3_bios" type="bool">false</merge>
	<merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
     </match>
```
```

     <match key="system.hardware.product" prefix_outof="6457;6460">
	<merge key="power_management.quirk.s3_bios" type="bool">false</merge>
	<merge key="power_management.quirk.s3_mode" type="bool">true</merge>
	<merge key="power_management.quirk.save_pci" type="bool">true</merge>
     </match>
```

At some point, standby worked on my first install.  Then, without changing anything, it began not working.  When entering standby the screen would go black, HD light would flicker for a few seconds, then would stop at a black screen with blinking cursor.  I can then press CTRL+F1 to return to console or CTRL+F7 to return to X, log back into gnome-screensaver, and everything is back.  When it was working, the moon LED (the ThinkPad sleep LED) would begin flashing almost immediately after pressing the standby button.

It seems to me as if some ACPI communication has been lost, like the ThinkPad hardware does not know that it needs to enter a sleep state.  But I may be wrong =)

Let me know what other info I can provide that would be of help.  Thanks!!

---

