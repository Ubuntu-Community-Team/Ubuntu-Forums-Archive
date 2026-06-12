---
title: "Print jobs sent to HP printer not being processed"
date: 2009-06-15
forum: Hardware
---

### Post by cajunaggie on 2009-06-15
I have a HP OfficeJet T45 printer that printed just fine under Ibis, though I could never get XSANE to recognize it as a scanner. After I upgraded to Jackelope, the printer stopped working. I get notification that the printing job has completed but nothing comes out of the printer. I can't test the printer under Windows, because XP doesn't support this printer either.

I used the default printer installation available through Ubuntu, and tried each of the four drivers provided there, none of which worked. I install the HP toolbox, but it doesn't recognize the printer. Running hp-setup through the shell with the sudo command doesn't find any devices either. I have tried all three options, USB, network/internet/ethernet, and Parallel (LPT) with no luck.

I found another thread that solved this by running hp-plugin. I tried that with no effect. 

*{aside-rant}*If you'll excuse to childish whining, I really do need printing capabilities for my university work and using the campus printing is costing me quite a bit. Given the difficulties I've had with printing, the GUI, and the warped sound quality (all still unsolved), Jackelope is shaping up to be the most frustrating distribution thus far. ](*,) *{/aside-rant}* Does anyone have anything they think might help?

---

### Post by tgalati4 on 2009-06-15
Change *warning* to *debug* in /etc/cups/cupsd.conf

tail -f /var/log/cups/error_log

Try to print and watch the terminal for interesting messages.

But, first, delete printer and reinstall using hp-toolbox.

---

### Post by cajunaggie on 2009-06-15
*But, first, delete printer and reinstall using hp-toolbox.*
I can't install using hp-toolbox. HP-toolbox can't find the device.

Output of tail -f /var/log/cups/error_log:
> E [15/Jun/2009:09:32:53 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:32:55 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:33:10 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:33:38 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:34:07 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:34:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [15/Jun/2009:09:37:27 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:37:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:37:35 -0500] cupsdAuthorize: Local authentication certificate not found!
E [15/Jun/2009:09:37:35 -0500] CUPS-Add-Modify-Printer: Unauthorized

---

### Post by Lou Jansen on 2009-07-22
Am having similar problem with HP Deskjet 5550.
When I print a test job it shows in print que, then after ~ minute a message appears that job has completed - although nothing comes out of printer.  Printer works fine on XP laptop


Output of tail -f /var/log/cups/error_log:
E [22/Jul/2009:07:35:04 -0500] Unable to find IP address for server name "lou-desktop"!
E [22/Jul/2009:07:35:45 -0500] cupsdAuthorize: Local authentication certificate not found!
E [22/Jul/2009:07:36:01 -0500] cupsdAuthorize: Local authentication certificate not found!
E [22/Jul/2009:07:36:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [22/Jul/2009:09:53:53 -0500] CUPS-Delete-Printer: Unauthorized
E [22/Jul/2009:09:55:08 -0500] [CGI] Unable to scan "@LOCAL"!
E [22/Jul/2009:09:57:05 -0500] cupsdAuthorize: Local authentication certificate not found!
E [22/Jul/2009:09:57:05 -0500] CUPS-Add-Modify-Printer: Unauthorized

Did this from a root login so should have had permissions?

Any ideas?

---

