---
title: "Konica Minolta bizhub C224e, CUPS, IPP - configuration with Account Track"
date: 2019-03-20
forum: Hardware
---

### Post by Argonisius on 2019-03-20
[COLOR=#333333]I'm trying to setup IPP printing on bizhub C224e and Ubuntu PC with Account Track feature.[/COLOR]

[COLOR=#333333]- Account Track is enabled on the printer -> I have a User name + PIN[/COLOR]
[COLOR=#333333]- IPP is enabled on the printer -> I know the IPP URI[/COLOR]
[COLOR=#333333]- IPP authentication is enabled (method: request-user-name) - by selecting this option I expect that I can use the same credentials for IPP print as I'm using with Account Track[/COLOR]
[COLOR=#333333]- I've added the printer to CUPS via the web interface, using URI found in the printer admin and PPD found on the support website[/COLOR]

[COLOR=#333333]The problem is that when I'm printing, the job is sent to the printer, CUPS tells me that it's completed, but nothing is printed. When examining the Job history on the printer's lcd screen I can see that the job is there, but there's "group authentication error". It seems that CUPS is not sending the right authentication info. My question is: where do I put the PIN code I'm using for authentication? I've tried setting the printer's device URI in format ipps://username: password@printer_ip/ipp, but it didn't work - I suppose that would work with the IPP authentication set to "Basic"? [/COLOR]

[COLOR=#333333]Thanks for any suggestions.[/COLOR]

---

