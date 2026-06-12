---
title: "Problem with Brother printer on Xubuntu"
date: 2023-06-14
forum: Hardware
---

### Post by Ralph L on 2023-06-14
I bought a Brother MFC-J805DW printer. It installed without problem and prints nicely. However, it has one major problem for me. When it is unused for a period of time (5 min for my setting) it goes into "shallow sleep mode". If I print something after 5 min, it comes out of shallow sleep and prints fine. However, after a second time period without use (in my case 1 hour) it goes into a "deep sleep" mode (Brother calls this "Auto Power Off", but the printer is not really off). Attempting to print when in deep sleep will not work and freezes the whole print system. In order to print I have to restart my Xubuntu 22.04 system. This is very annoying!!!!!! If I turn the printer off with the on/off switch (the printer is really off now) and try to print, the printer, of course, will not print. But, with the computer holding the print job in the print queue, I press the on/off switch and turn the printer back on, and release the job in the print queue, the printer will print it.

The net of this is that the printer works fine in the "fully on" mode, in the "shallow sleep" mode, and in the fully off (done with the on/off button), but not in the "deep sleep" (auto power off) mode. 

I talked to Brother and the rep said they have the same problem with Windows, and said they have to take the printer off line and reconnect it to wifi to get it to work.

Anybody else have this problem with Brother printers on ubuntu (xubuntu)???? Now I am wishing I had stuck with HP printers even though I don't like a lot of things. At least their software (HPLIP) worked.

Any help appreciated........

---

### Post by QIII on 2023-06-14
Moved to Hardware from [https://ubuntuforums.org/showthread.php?t=2482987](https://ubuntuforums.org/showthread.php?t=2482987) since this is now a support question.

---

### Post by Ralph L on 2023-06-15
QIII

You moved this to the Hardware Forum. I don't think this is a hardware problem, but rather is a software problem. Could you move this to the General Support Forum so that I get more views of my problem.

Thank you

---

### Post by SeijiSensei on 2023-06-15
You mentioned having an issue with wifi. Have you tried connecting the printer directly to your router with an Ethernet cable?

---

### Post by Ralph L on 2023-06-15
SeijiSensei

Thank you very much for your response!! No, I haven't tried connecting other than thru wifi. I could try that as an experiment, but I really wouldn't like it as a long term solution, since my computer is a laptop, and I like to roam around the house using it. But maybe connecting it through ethernet,  seeing its behavior, and reporting it to Brother might help them solve what I think is a software problem.

I am anxious to get responses from people who have the same model, or similar, printer to see if they have the same problem.

Thanks again,
Ralph

---

### Post by SeijiSensei on 2023-06-24
I have mine wired directly to the router and assigned it a static IP address. I can print to it from any device on my network, including my Android phone with the Brother app.

---

### Post by mIk3_08 on 2023-06-25
Same here with SeijiSensei. I do have my Brother printer/scanner  connected directly to my router via wifi. Works smoothly to my Linux  Ubuntu System with no issues. So far so Good! The scanner works  perfectly with Document Scanner and xsane "featureful graphical frontend  scanning application" you just have to configure it with the IP  assignment to be able to work simultaneously on you Linux Ubuntu System.  Regards and cheers.

---

### Post by brian_p on 2023-06-25
Consult the printer's manual. I think the printer control panel can be used to alter the behaviour you are experiencing. See under General Settings.

---

### Post by Ralph L on 2023-07-01
Again, thanks to everybody who replied to this thread!!
I am still having problems. The printer hangs and everything goes into the print queue as "pending". I can't release it. If I restart my computer, it will usually (but not always) print--until it goes into the auto-power-off (deep sleep) mode. Sometimes it will resume printing from this mode, sometimes not.
When ever the printer does print and I am watching the "Printer" window, a red exclamation point will come up. I am guess it is reporting some sort of error. Does anybody know what the meaning of the red exclamation point is????????????

There are a number "Settings" that can be changed under the Printers>Properties menu. Anybody know how all these are supposed to be set. I don't and can't find any documentation. For example, what should be in the Device URI: mine says "implicitclass://Brother_MFC_J805DW/" This seems like an odd URI. I am used to something like 192.168.1.3. Anybody know what should be in the Device URI field???????

The Server>Connect field can be set to either /run/cups/cups.sock or localhost. Anybody know which is correct??????

There a whole bunch more settings under Printers>Properties that I don't understand, but it would be helpful if somebody knew the answers to the above questions.
Thank you,,,,,,

Edited to change URL to URI. As was pointed out by a post below the Brother Setting menu uses URI.

---

### Post by Ralph L on 2023-07-05
I did a bit more attempting to diagnose my Brother printer problems. What I did is listed below. Anybody have any ideas on what the problem could be????

When the printer gets into a state when it won't recover from Auto Power-Off (deep sleep), the Printer>Settings lists Printer State as "Idle". Printer>Properties>Policies has the Enabled checkbox checked.

When I try to print, the status comes up as "processing". However, after a minute or 2, a Print Error window comes up and the Printers>Setting>Printer State changes to:  "Stopped - No destination host name supplied by cups-browsed for printer "Brother_MFC_J805DW", is cups-browsed running?" Also, Policies>State Enabled checkbox is change to unchecked, when the error is issued. 

The Print Error window has an option to diagnose the error. If I select "Diagnose", it asks me to choose a printer. Three printers are listed, two of whuich I have no clue of where the software got them, since they are not listed in "Printers". The 3 are "not listed", "Brother_MFC_J805DW", and "Brother_MFC_J805DW_asp1". Only "Brother_MFC_J805DW" is listed in Printers, so I choose it for the diagnostic. NOTE: "asp1" is the name of my computer. I click "Forward" on the diagnostic and it says:

Queue Not Enabled

The queue 'Brother_MFC-J805DW is not enabled. The reason given is: 'No destination host name supplied by cups-browsed for printer 'Brother_MFC-J805DW', is cups-browsed running?.
To enable it, select the Enabled checkbox in the ;Policies' tab for the printer in the printer administration tool. To start this tool,select System->Administration-> Print Settings from the main menu.

Yes the Enabled checkbox was not set, since the Print Error just cleared it. So I set it to enabled but this didn't cause the job to print. However, either way nothing will print until I reboot the computer.  
Anybody have any idea of what could be causing this problem???????????

---

### Post by aljames2 on 2023-07-05
The cups-browsed is a daemon that searches your network for all remote  printers, and including what your system sees and thinks is an available remote printer, and  attempts to make them available for you to print to. You could try to stop this service, then  power off your printer, then power it back on, let it make all it's  noises, wait 2 minutes, then try to manually add your printer via the Xubuntu "Settings"  --> "Printers" --> "Add" printer.

To stop the cups-browsed daemon:
```
systemctl stop cups-browsed
systemctl status cups-browsed
```

Others have found success purging and reinstalling the daemon, but I would try to stop it first and see if that leads you to some progress.
[https://askubuntu.com/questions/1128164/no-suitable-destination-host-found-by-cups-browsed](https://askubuntu.com/questions/1128164/no-suitable-destination-host-found-by-cups-browsed)

---

### Post by mIk3_08 on 2023-07-06
> **Ralph L said:**
> 
There are a number "Settings" that can be changed under the Printers>Properties menu. Anybody know how all these are supposed to be set. I don't and can't find any documentation. For example, what should be in the Device URL: mine says "implicitclass://Brother_MFC_J805DW/" This seems like an odd URL. I am used to something like 192.168.1.3. Anybody know what should be in the Device URL field???????

The Server>Connect field can be set to either /run/cups/cups.sock or localhost. Anybody know which is correct??????

There a whole bunch more settings under Printers>Properties that I don't understand, but it would be helpful if somebody knew the answers to the above questions.
Thank you,,,,,,

It should be Device URI not Device URL mine, is "ipp://Brother_DCP-T500W._ipp._tcp.local/" 
Just curious, Are you using some Firewall on your desktop? In my case, When my firewall is enabled I can't print? it says, printing in queue but the printer won't received any printing data. But when I disable my firewall it automatically prints. 
My Brother printer/scanner say's receiving data for printing. 
Regards and cheers.

---

### Post by brian_p on 2023-07-06
It is unclear from the responses whether the sleep mode is or is not is controllable from the front panel. Anyway, you could try a different print queue set up. It doesn't get any more basic than this.

Execute ```
driverless
``` The output is a URI. **Substitute** this URI in ```
lpadmin -p J805 -v "URI" -E -m everywhere
```

Test printing to J805.

---

### Post by Ralph L on 2023-07-31
Thanks again to everyone who replied to this post. I appreciate it very much. I followed the instructions from brian_p in Post 13 of this thread and now my printer seems to work (at least for the last 2 days). Thank you brian_p. i don't understand the changes made. Under Printer>Properties I see the following changes: 
Device URI: "implicitclass://Brother_MFC_J805DW/" became "ipp://BRW30C9AB632C45.local:631/ipp/print"; 
Make and Model: "Brother MFC-J805DW, driverless, cups-filters 1.28.15" became "MFC-J805DW - IPP Everywhere".

Its all greek to me, but it seems to work. Incidentally, I exchanged email with Brother support. They told me that my Internet router was bad and that I needed to reset it to factory configuration. I have set it to give priority to my Voice Over Internet phone (or at least I hope that is what I did), and did not want to change it. I don't know how the support guy could come up with "bad Internet", but I guess when they don't know how to fix something, they just make something up.

Thank you again,

---

### Post by mIk3_08 on 2023-08-02
> **Ralph L said:**
> Thanks again to everyone who replied to this post. I appreciate it very much. I followed the instructions from brian_p in Post 13 of this thread and now my printer seems to work (at least for the last 2 days). Thank you brian_p. i don't understand the changes made. Under Printer>Properties I see the following changes: 
Device URI: "implicitclass://Brother_MFC_J805DW/" became "ipp://BRW30C9AB632C45.local:631/ipp/print"; 
Make and Model: "Brother MFC-J805DW, driverless, cups-filters 1.28.15" became "MFC-J805DW - IPP Everywhere".

Its all greek to me, but it seems to work. 
Thank you again,

If your query has been sorted then you can mark this thread as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. 
Regards and cheers.

---

