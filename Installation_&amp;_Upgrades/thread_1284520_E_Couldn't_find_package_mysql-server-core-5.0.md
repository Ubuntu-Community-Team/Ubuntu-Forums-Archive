---
title: "E: Couldn't find package mysql-server-core-5.0"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by JackJr on 2009-10-06
Hi, I'm very new to all of this, so please bear with me.

I tried installing Rails following the steps in this url [http://www.hackido.com/2009/04/install-ruby-rails-on-ubuntu-904-jaunty.html]("http://ubuntuforums.org/sudo%20apt-get%20install%20ruby%20ri%20rdoc%20mysql-server%20libmysql-ruby%20ruby1.8-dev%20irb1.8%20libdbd-mysql-perl%20libdbi-perl%20libmysql-ruby1.8%20libmysqlclient15off%20libnet-daemon-perl%20libplrpc-perl%20libreadline-ruby1.8%20libruby1.8%20mysql-client-5.0%20mysql-common%20mysql-server-5.0%20rdoc1.8%20ri1.8%20ruby1.8%20irb%20libopenssl-ruby%20libopenssl-ruby1.8%20libhtml-template-perl%20mysql-server-core-5.0")

After step 3[FONT=monospace], everything looked OK except for this part of the message: 

E: Couldn't find package mysql-server-core-5.0

Suggestions?
[/FONT]

---

### Post by Partyboi2 on 2009-10-07
Hi, that package is only available for Jaunty from the Ubuntu repositories. Are you using Jaunty or another version of Ubuntu? 
If you are unsure what version of Ubuntu you are using you can open a terminal and find out by typing
```
lsb_release -d
```

---

### Post by JackJr on 2009-10-07
Thanks.  I checked it out, and I am using:
Ubuntu 8.04.3 LTS

There's no particularly good reason I am using this version of Ubuntu.  I just saw it in this youtube video: [http://www.youtube.com/watch?v=S30OUYsu2Qo&feature=player_embedded](http://www.youtube.com/watch?v=S30OUYsu2Qo&feature=player_embedded)

I did find these other instructions:
[http://agileweb.wordpress.com/2008/07/18/how-to-install-rails-21-on-ubuntu-in-5-steps/](http://agileweb.wordpress.com/2008/07/18/how-to-install-rails-21-on-ubuntu-in-5-steps/)

I'll give that a shot and update here if it works out ok.  Thanks

---

