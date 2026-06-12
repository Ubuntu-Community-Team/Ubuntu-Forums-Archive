---
title: "HellaNZB 502-Authentication Error"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by fzfowler on 2009-04-09
Hello,

I am running Ubuntu 8.10 and hellanzb-0.13-3ubuntu1.

One possible problem was I first tried installing hellanzb from tar.gz from the site. I tried to get rid of everything and installed my current version through Synaptic but it still hasnt solved these problems. 

I enabled logging and this string of errors continually repeats:

2009-04-09 03:46:29,903 newsdemon[0] CONNECTION MADE
2009-04-09 03:46:30,059 newsdemon[0] MODE READER successful
2009-04-09 03:46:30,219 newsdemon[0] AUTHINFO failed: 502 Authentication Failed
2009-04-09 03:46:30,220 newsdemon[0] CONNECTION LOST

I know that someone is going to say that I have typed my username and password into the hellanzb.conf but I have checked and double checked all the information. The info works on my windows machine running NewsLeecher and I installed Klibido and the username, password and server settings worked.

I have tried all the ports that my server provides, have tried several different nzbs, I am at the point where I am probably going to try to use NewsLeecher in wine. 

Below is the defineServer part of my hellanzb.conf file, any help is greatly appreciated.

defineServer(id = 'newsdemon',
             hosts = [ 'us-secure.newsdemon.com:80' ],
             #hosts = [ 'us-secure.newsdemon.com:563', 'useast.newsdemon.com:119' ],


             username = '******',
             password = '******',
             #username = None,           # no auth
             #password = None,

             connections = 1,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = True
             )

---

### Post by cb951303 on 2009-04-09
can you try with [lottanzb]("http://www.lottanzb.org/") too (it uses hellenzb as a backend)
but first delete the .hellanzb directory in home.

---

### Post by fzfowler on 2009-04-09
I tried installing LottaNZB but I am having the same problem. 

One more update, I installed ninan and am having the same problems, I dont know how to log the errors in the program but I am getting zero download speed. There must be something that I am missing as far as a dependency that would allow me to connect to these servers. That is my only guess.

I really need to solve this problem because NewsLeecher on Wine sucks! And I really dont want to have to boot virtual box just to use newsgroups.

Thanks!

---

