---
title: "Evince, or Document Viewer cannot find firefox when clicking hyperlinks in PDFs"
date: 2008-09-16
forum: General Help
---

### Post by mdecler2 on 2008-09-16
When I click on a hyperlink in a PDF using evince (AKA Document Viewer), evince looks for /usr/lib/mozilla-firefox/firefox which doesn't exist anymore due to an upgrade from Dapper to Hardy and the new Firefox version 3.0.1.

I could make that folder and put a symbolic link to the firefox binary, but I am looking for a more elegant solution. I have been trying to look for an evince configuration file but have been unsuccessful, and the evince man page is anything but helpful.

Anyone have any ideas?

---

### Post by ryanhaigh on 2008-09-18
Seeing as Evince is a gnome application I would expect that it is looking for the default browser as defined in System>Preferences>Preferred Applications. Unfortunately I am not on my Ubuntu machine to confirm this but it is quite easy to confirm that the browser defined there points to your current Firefox.

---

### Post by mdecler2 on 2009-11-05
I never replied to how I solved this! I will take a stab at it now for those that may need this:

I took ryanhaigh's suggestion to heart, thinking that it might be the Ubuntu OS rather than evince that was sugesting the incorect location to the browser.

The following link was helpful:
[http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/](http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/)

Solution:
to summarize, use the ```
sudo update-alternatives --config x-www-browser
``` and select the number for the corresponding browser you want to be default. In my case it was /usr/bin/firefox-3.0

---

### Post by tapin13 on 2011-06-26
> **ryanhaigh said:**
> System>Preferences>Preferred Applications. Unfortunately I am not on my Ubuntu machine to confirm this but it is quite easy to confirm that the browser defined there points to your current Firefox.

It's work!!! thanks! :guitar:

---

### Post by raysa on 2012-10-29
My problem seems a bit different, in that hyperlinks in pdf files viewed in Evince don't even register. The curser doesn't change when over the link, and no link info appears. So it's not a case of not being able to find Firefox - it's not even recognising that a link exists.  Any thoughts?

Xubuntu 12.04, Evince 3.4.0

---

### Post by overdrank on 2012-10-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

