---
title: "Cannot Open New Firefox Windows"
date: 2008-09-10
forum: General Help
---

### Post by Zybthranger314 on 2008-09-10
When I upgraded to 8.04 and started using Firefox v.3 a problem started with opening new windows in Firefox; namely it doesn't happen. I select 'Open New Window' and nothing happens. When I click the shortcut to Firefox, which normally opens a new window, the computer seems to start up on opening up a window, but after 15 seconds it stops.

Reinstalling FF3 and 8.04, along with disabling and uninstalling all extensions have not created a solution. So I'm stumped.

I also posed the question in the FF Support Forums.  [http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=155008&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=155008&forumId=1)

---

### Post by NT4usB on 2008-09-10
Silly question but did you look behind the current window?
Ubuntu likes to leave newly opened windows behind existing ones.
Tried the keycommand Ctrl+n to get a new window?
Tried right click a link and open in new window?
When I (accidently) click the shortcut icon, Ubuntu winges at me that I already have a Firefox instance open so if I want to open a new one, I must close the old one first...
Other than that, I can get a new window the other ways... but I'm not running 8.04 or Fx3.
There's a bunch of 'about:config' settings that influence how windows act. Might poke around there with 'windows' as the filter word.

---

### Post by Zybthranger314 on 2008-09-11
Nope, it isn't that obvious.

In about:config with 'window' as the filter, everything is default except for

intl.charsetmenu.browser.cache; user set; string; UTF-8, ISO-8859-1, windows-1257, windows-1252, windows-1251

which I don't think is the problem.


Here are the only things in about:config that look relevant to opening a new window.

browser.link.open_newwindow;default; integer; 3
browser.link.open_newwindow.restriction;2

---

### Post by NT4usB on 2008-09-11
All that looks normal.
There used to be a setting along the line of force links that try to open a new window to open in a tab. I don't see it in v3. If that were the default now, with no option to change it, might explain your issue.
Doesn't look like your ff support post is getting lots of activity. Might try asking at the news.mozilla.com newsgroup mozilla.support.firefox
Lots of activity and several *nix users there.
I'm out of ideas...

---

### Post by putnins on 2008-09-11
I am having the same problem. If I select "new window" from the file menu, firefox consumes 100% of the CPU until I kill the process. I've tried uninstalling and re-installing with apt-get, but it still behaves the same. No problem opening new tabs in the same window.

---

### Post by wilfredtee on 2008-11-17
I am facing the same problem. I've tried the following methods to open a new firefox window and it does not work.
[LIST=1]
[*]via gnome start menu
[*]via command line "firefox"
[*]via right-click open in new window
[*]via firefox file menu - open new window
[*]via shortcut ctrl-n in firefox
[/LIST]

all of the methods used above does not open a new window.

firefox is version 3.0.4 I'm running on ubuntu hardy heron LTS 8.04

what other information is needed to help resolve this issue?

:(

---

### Post by wilfredtee on 2008-11-25
bump?

---

