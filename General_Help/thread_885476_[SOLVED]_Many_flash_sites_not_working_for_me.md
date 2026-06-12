---
title: "[SOLVED] Many flash sites not working for me"
date: 2008-08-10
forum: General Help
---

### Post by df9517 on 2008-08-10
I have Hardy 32 bit.

Youtube works well but some flash doesn't work, examples:

Air app installation: [http://www.adobe.com/cfusion/exchange/index.cfm?event=extensionDetail&loc=en_us&extid=1433018](http://www.adobe.com/cfusion/exchange/index.cfm?event=extensionDetail&loc=en_us&extid=1433018)

Google currency graph: [http://finance.google.com/finance?q=USDSEK](http://finance.google.com/finance?q=USDSEK)

Does it work for you, if so how can I fix it?

I have macromedia flash and just downloaded the latest installer and run it from adobe. Still same problem.

Anybody who can help out with this?

Thanks

Daniel

---

### Post by silkstone on 2008-08-10
Both sites display perfectly for me although the first one tells me that the application is not available for my system. The graph and slider in the second site work fine.

I have installed Flash 10 beta 1 using the procedure towards the end of the following guide, under the heading 'Troubleshooting - Adobe Flash Player'.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The latest version is beta 2 which some people find does not work as well. You may be able to find a download of beta 1 if you search around. It's only the file libflashplayer.so that you need if you follow that guide.

---

### Post by df9517 on 2008-08-10
Many thanks, closer but still not solved.

I followed the instructions on the page.

Now I have 3 plugins enabled 2 plugins of the 9.0 type and one of 10 beta type.

Still result is same as previously. If I disable the two 9.0 flash doesn't work at all.

Please kick me in the right direction.

/Daniel

---

### Post by df9517 on 2008-08-10
Okay I solved this.

I understand the sole problem in the beginning was that flash 9 is not good enough for some sites.

To remove the flash plugins i had I did:
1) wiped out .mozilla (not sure this was necessary)
2) removed all with flash in synaptics

After that all flash 9 plugins was gone in Firefox

Then I installed flash 10 beta.

---

