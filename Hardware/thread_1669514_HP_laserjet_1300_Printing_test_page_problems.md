---
title: "HP laserjet 1300 Printing test page problems"
date: 2011-01-17
forum: Hardware
---

### Post by IPEX-731BA5DD06 on 2011-01-17
I have a problem that have been re-current since ubuntu 8.04.

Printer is HP laserjet 1300.

I CAN!!! install the printer software, both the HPLIP-3.10.9 (note, don't have a space in folder headings..ie Printer drivers should be Printerdrives )

See.

I've also installed through System/Admin/Printing. \\:D/


In _**BOTH**_ Cases, when I try to print _**ANYTHING**_ I can only print out the message, below the header space, of:8-[

%!PS-Adobe-3.0
                        %%LanguageLevel1: 2
                                                          %%DocumentSuppliedResource: (atend)
                                                                                                                      %%Document


Note recorded Verbatim. next line is continued directly below the above line. 
i.e. 3.0, 
[space]%%LanguageLevel1: 2
[ space, space ,space, space, ]%% (get the idea):KS

It then proceeds to then run through all available paper, if not stopped, infinitum.

Current Operating system is 10.4.1

Further data;:popcorn:

Printer is recognised correctly.
Cups have been installed. cups 1.4.6 checked, compiled and installed. Yes done 1st
hplip 3.10.9 has been installed, checked, tried, cursed at  and un-installed. (aarrrgghhhh so frustrating)
Help documentation has been referenced, Bah...nothing.
Connected Via USB, DIRECTLY into computer, or Via HUB same problem.
Printing from Open office, printer is recognised and same output.
Clean heads option via HPLIP does_** NOTHING**_ (Ah ha, getting somewhere now)
Printing test page causes above problem. (Boo this sucks, hey, I'm back at start again :confused:)

I've tried 1300, 1300n, 1300postscript. 

as far as I see (limited understanding) postscript is enabled and available??

any suggestions, advice or offers of _**MONEY!!!!**_ are gratefully accepted. ):P

---

### Post by IPEX-731BA5DD06 on 2011-01-19
):P Thanks for all the money, my problem had been solved. Here's how;

Change make and model to alter driver for printer to:

HP Laserjet 1300-CUPS+Gutenprint V5.2.5 Simplified [en] Current.           #-o, should have figured this one out myself quickly. :oops:

this is the 3rd of 4th driver in the list I had, for 1300 (no letters) of 10 drivers #-o

Probably only real problem now is the duplex printing, it won't start duplex when I press the flashing button as before, but waits 1 minute to automatically take in the paper.

Small problem if that's how it works, but flashing button, works under windows for duplex printing?? oh well.[-(

Oh have to install CUPS as well, I complied it or checked it, not sure which, but went through a lot of checking.

HPLIP has been installed as well, all working fine.

Printing now working, Text pages, normal printing from Open office, :P:guitar:

---

