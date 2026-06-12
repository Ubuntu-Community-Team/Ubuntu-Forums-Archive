---
title: "Ruby on Rails 1.0 trouble"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by Nolgthorn on 2006-02-07
Hello, I used to have Rails 0.8 installed through the repositories and it was working great. I needed to have version 1.0 for several features important to Rails development, so I uninstalled Rails via Synaptic and followed the guide [located here](https://wiki.ubuntu.com/RubyOnRails).

After I was finished I went back to try and start a webrick server, but now I keep getting this error:

> $ script/server
./script/../config/environment.rb:50:in `require': no such file to load -- active_support (LoadError)
        from ./script/../config/environment.rb:50
        from script/server:44

I have no idea how to get rid of it, I've tried restarting the computer and everything (force of habit from when I was using Windows.) I've also tried the gems command "sudo gem update --include-dependencies rails" everything seems to install fine. Please help me.

I have this huge project I'm working on and I can't find anyone with a similar problem anywhere. It's really bugging me.

---

### Post by Nolgthorn on 2006-02-07
I experimented a little bit and found that by creating a new rails project that I could start a webrick server on it. So I created a new project, transferred all of my important files from the old project to the new, and now it works again.

Just a heads up for anyone who might come into the same troubles I have.

Also just as a note the 1.0 installation was a success and I can use all of the new features.

---

