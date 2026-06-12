---
title: "zlib conflict when installed from source"
date: 2008-10-17
forum: General Help
---

### Post by The Neurochild on 2008-10-17
Hey guys!

I'm trying to build my Ruby on Rails environment and i'm buildig everything from source. I installed the Apache HTTP Server 2.2.9: no conflict. Before installing OpenSSL 0.9.8i: I suddenly saw there's the previous version installed in Synaptics, but if I remove it, it'll affect the ubuntu-desktop component and the ssl-cert. But anyway, I removed it and installed the newer one: no conflict. Proceeded with zlib 1.2.3, i didn't uninstalled that one becase if I do, I would destroy Ubuntu. I installed that... *DING*. There is certainly a conflict.

The truth is... It didn't died on me until now. I tested it in Debian and even RHEL5, but in Ubuntu, when I installed the version I have (dated 18-07-2005) and restarted my laptop, I get a horrible surprise. It doesn't access to the login screen on startup. Normally, it would take 4 second for the screen to show up, but after installing that version of zlib, it takes forever... leaving Ubuntu useless.

The Fact: I need zlib to use Ruby and the rest of the components from source too and make it work correctly. It didn't failed on me with those Linux distros, but it did in Ubuntu.

What can I do now? I feel sick and tired of doing this trial and error.

I'm attaching you the the installation procedure I'm doing on my machines until zlib. Maybe you can suggest me something.

Greetings...

The Neurochild

P.D.: I have a source that supports it! [Here]("http://www.nabble.com/Re:-install-question-RE:ruby-1.8.6,-rubygems-1.2.0,-rails,-mongrel-on--redhat-4-td19461111.html")

I have Ubuntu 8.04.1 LTS Hardy Heron BTW.

---

