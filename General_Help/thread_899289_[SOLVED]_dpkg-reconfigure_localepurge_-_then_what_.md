---
title: "[SOLVED] dpkg-reconfigure localepurge - then what &amp;amp; how?"
date: 2008-08-24
forum: General Help
---

### Post by b9k9kiwi on 2008-08-24
I don't like to waste other users time so I have first searched and searched these forums but I have not found any responses (to others with similar problems) that solve mine.

I am failing to install software via apt-get because (according to error message) I need to configure dpkg using the command sudo dpkg-reconfigure localepurge.

Okay, I do that, and I get to the language selection dialogue but cannot find any way to highlight the language selections I want make.  One message thread says that a right-mouse-click will highlight each selection - but, in my case, that just brings up the desktop menu.  I've tried to use my imagination - used tab, backspace, asterisk etc, etc, to no avail.

So, in short, my question is - how do you highlight (select) language selections in the first dialogue to come to when running dpkg-reconfigure localepurge?

Please :)

---

### Post by fooman on 2008-08-24
you should be able to use the up and down arrow keys to scroll through the list.  scroll down to the language of your choice so that it is highlighted,  then use "tab" to choose "o,k,".  now just hit enter.

---

### Post by b9k9kiwi on 2008-08-24
> **fooman said:**
> you should be able to use the up and down arrow keys to scroll through the list.  scroll down to the language of your choice so that it is highlighted,  then use "tab" to choose "o,k,".  now just hit enter.

Mmmmmmmm ... I scroll down okay with the arrow key - a highlight block appears between the square brackets - the tab key then takes me to the OK, then enter.  At this point I get a message asking me to confirm that I wish to purge ALL languages (i.e. no particular language has been selected.

---

### Post by oldos2er on 2008-08-24
Use the space bar to select and deselect languages.

---

### Post by b9k9kiwi on 2008-08-24
> **oldos2er said:**
> Use the space bar to select and deselect languages.

Of course!  The only key I hadn't tried :)

Seems to have worked (I didn't get any terminal output, but never mind).

Thanks.

---

