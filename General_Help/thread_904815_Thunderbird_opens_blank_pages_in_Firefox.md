---
title: "Thunderbird opens blank pages in Firefox"
date: 2008-08-29
forum: General Help
---

### Post by uba704 on 2008-08-29
Hi,

I have a few computers which have been running Kubuntu Dapper 6.06 for about 1.5 years now. Quite recently, like 1-2 months ago, Thunderbird have started to open weblinks in emails that you click on in Firefox as blank pages the first time Firefox is started. When Firefox is running the weblinks opens up correctly in Firefox when clicking on them in Thunderbird.

That means every time I want to open a certain page from Thunderbird and Firefox is not running then I need to click on the weblink two times and will get two tabs in Firefox, one blank "(Untitled)" and one with the desired page.

Any idea how I can correct this? I suppose this has started to happen because of an Ubuntu update I got with 'apt-get update ; apt-get -y dist-upgrade' about 1-2 months ago since I run that every morning. I have tried with different user accounts and also to remove ~/.mozilla and ~/.mozilla-thunderbird but the problem is still there.

Thanks for any help!

---

### Post by uba704 on 2008-09-01
What exactly happens when Thunderbird launches Firefox? Is Thunderbird invoking /usr/bin/firefox with the URL as an argument? I have not adjusted the Firefox installation in any way and the problem is still there even if I remove ~/.mozilla and ~/.mozilla-thunderbird .

$ which firefox
/usr/bin/firefox

$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 22 2008-07-17 17:49 /usr/bin/firefox -> ../lib/firefox/firefox

$ ls -l /usr/lib/firefox/firefox
-rwxr-xr-x 1 root root 7732 2008-07-15 18:28 /usr/lib/firefox/firefox

The file /usr/lib/firefox/firefox seem to be a wrapper script for Firefox and be looking at the timestamp of that file, 15 July 2008, it seems likely to me it was about that time the problem started.

Thanks for any help on how I can solve this since it is quite annoying.

---

