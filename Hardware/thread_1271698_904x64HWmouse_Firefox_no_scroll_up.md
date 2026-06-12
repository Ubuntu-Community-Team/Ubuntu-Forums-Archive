---
title: "904x64:HW:mouse:: Firefox:: no scroll up"
date: 2009-09-21
forum: Hardware
---

### Post by xerman on 2009-09-21
Hello there:

I have several ubuntu machines, and i found this issue happening just to one machine and just with Firefox.

Scenario:
1- Browsing web pages through Firefox.
2- Scroll down using wheel works well
3- Scroll up using wheel does not work well. Scroll up produces "go to previous/Back".

This happens just on the Firefox Window. In Firefox preferences can scroll up down with no issues. Everywhere in the system can scroll up/down with no issues.

Epiphany browser (Gecko) has no issues either when scrolling up.

So seems Firefox related.

Any help would be appreciated.

Best regards

---

### Post by xerman on 2009-09-29
Hello there again:

New issues noticed:

FIREFOX
1. When the site is the first one of the tab, scrolling up works as it should, with no issues at all.
2. When there is an option to go back to a previous site or forward to a next site behaviour of mouse scroll up is strange:
  2.1. Sometimes scroll up does a Go Back to previous page.
  2.2. Sometimes scroll up does a scroll up and refreshes the address so i presume is reloading the page.

NEW: EVOLUTION
This weird scroll behaviour has been noticed also in evolution:
1. While in the inbox part of the window (in Mail) scrolling down-up across folders, scroll up produces "select the folder the mouse is over".

While thinking before was a Firefox issue, it seems the issue is more X related than FF.

Best regards.
Xermán

---

### Post by xerman on 2009-10-07
New things:

I just updated the machine not suffering from this issue to ubuntu 904x64 for desktop use.

I have a server with 904x86_32 and the desktop now with 904x64. Both machines are using same keyboard-mouse through a KVM switch. After paying attention to what happens, i found out the following:

1- If i turn on desktop pc and select desktop pc on the KVM (and once it is on, and logged in, i turn on server), the desktop pc will not suffer the weird scroll issue. But the server will suffer. So on desktop, Evolution and Firefox will behave well; but on the server the scroll up produces the weird behaviour.

2- If i turn on server pc and select server pc on the KVM, (and once it is on, and logged in, i turn on desktop), is the server the one with no issues.


So seems, at least in this case an issue related to the KVM (D-Link). This i came to because i turned on desktop pc and at first did not notice the issue, but sometimes scroll issue appeared, so finally i THINK, i am not sure yet. I will keep testing.

Regards.
Xermán

---

