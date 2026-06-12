---
title: "trouble installing &quot;driverless&quot; printer  -- Canon TR8620a"
date: 2023-11-30
forum: Hardware
---

### Post by ishmael3 on 2023-11-30
Hi all,

Stop me if you've heard this one...  having trouble getting printer to function with Ubuntu.  Any help getting me on track would be appreciated. Hoping to avoid using OEM driver -- in past have had good luck with Linux options.

Running Ubuntu 20.04, the printer is a Canon TR8620a (driverless). I have tried installing using printer settings of "wireless direct" and "wired lan." Have tried installing with "Printers" (System-configure-printer), and through Settings > Printers, and with localhost:631. All attempts recognize the printer and correctly identify it as a Canon TR8600 series driverless printer, and locate it on the local network. Each attempt proceeds a little differently, but after identifying and locating the printer all fail. No print response.  

**Installing through Printers (system-configure-printer)** sees the printer, and recognizes connection as "Driverless IPP." When I click "Forward" the system processes a short time then opens a new window with Printer Name (reads "printer"), Description (shows blank), and Location (shows blank). When I click Apply, window pops up saying **"CUPS server error," **only choice is to click OK. No printer installed.

**Installing through System > Printers**, finds printer, which seems to install when I select it, then window opens  saying **"Failed to add new printer."** Plus a second window opens saying Ubuntu has experienced an internal error with a long details list that I don't understand much of. However, an interesting line was: [B]*[CGI] Unable to create PPD file. Could not poll sufficient capability from the printer (ipp://TR8600%Series._ipp._tcp.local/,ipp://veriton-X4610G.local:6000/ipp/print) via IPP!*
[/B]
**Installing with localhost:631** proceeds smoothly. Immediately recognizes printer and location. Allows me to choose Make: "Canon" and  Model: "Canon TR8600 series - IPP Everywhere" (only method that shows this particular model choice). After I accept default options, printer appears installed and ready to go. Window says "Idle, Accepting Jobs." But if try to print anything, processing just continues until job is canceled, message in Jobs bar (bottom of localhost:631) says **"Unable to  get printer status."**

Not sure how to interpret failure messages: "CUPS server error," "Could not poll sufficient capability of printer,"  "Unable to get printer status." And not sure how to diagnose problem. Any ideas appreciated.

---

### Post by ishmael3 on 2023-12-09
Though not exactly a solution to original question -- installing printer on 20.04 -- the solution to my problem was simply upgrading to 22.04.3.  
 
 With 22.04 the printer installed instantly, far better than with any previous printer/Ubuntu combination.  Plus initial color prints have smoothly graded tones, neutral grays and accurate color (Hallelujah!) -- again, unlike any previous Linux experience.  
 
 The driver that automatically loaded is "driverless, cups-filters 1.28.15 (color, 2-sided printing)." That particular driver was not available with 20.04. I'd hoped to use the "IPP Everywhere" driver just because I love the idea of a truly universal solution. But there are rumors that Canon may not even support the trademarked "IPP Everywhere" for their "driverless" printers.
 
 There is also a package that comes with 22.04 called ipp-usb, which is not available for use with 20.04. According to the "CuPSDriverlessPrinting" page ([here]("https://wiki.debian.org/CUPSDriverlessPrinting")) ipp-usb has some particular use with driverless printers. Don't know if it had anything to do with my situation.  

 So, just to mention again: hooking up a Canon TR8620a printer using a wired (usb) LAN connection and (now) running Ubuntu 22.04.3.  
 
 Happy holidays!

---

### Post by ishmael3 on 2023-12-09
Sorry. Couldn't find where to mark "SOLVED."

---

### Post by oldfred on 2023-12-09
Above first post.
Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

This may have been issue.
ippusbxd is decidedly sub-optimal. Even its author would support your removing it from your system. 
It has been replaced by ipp-usb in later editions of Ubuntu.

---

