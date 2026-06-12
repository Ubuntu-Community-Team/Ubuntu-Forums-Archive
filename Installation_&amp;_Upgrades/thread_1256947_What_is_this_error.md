---
title: "What is this error?"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by red33m on 2009-09-03
I try to apt-get update, it gives me this and then it stays there forever.....
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty Release.gpg
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/universe Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty Release                                
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) jaunty-updates/multiverse Sources             
99% [Connecting to akirad.cinelerra.org (78.47.64.240)]  

Ithink I have to remove akirad.cinelerra.org...but how?

---

### Post by presence1960 on 2009-09-03
may not be an error, maybe the site for cinelerra is down or overloaded. I would wait a while and try again.

---

### Post by grungedoobie on 2009-09-03
This post says "[SOLVED]", however, I am not seeing any context which solves anything.  The wait and try it again later philosophy works most of the time, but if you've been staring at the error for almost 24 hours it would be nice to make it go away, because the link error ties up the updater.

Here's what I've found.

"akirad.cinelerra.org"

This is a community repository maintained by people who are passionate about video editing software.  "Cinellerra" being their num-da-plum."

I noted that their repository activation went down yesterday.  Recently tried it, and still a no-go.

Here is their repository page:

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

Just in case you want to try refreshing the repository link in case something has been changed.

If you want to bypass the error, just remove or "un-select" Cinelerra from repository.  When you're ready to give it another try, just put the repository back.  If you're not sure how to do that, just holler out what your linux flavor is and we'll see if we can help.

The Grunge

---

### Post by red33m on 2009-09-03
Thanks for the interest mate...I be passed the error on my own thats why I wrote solved....I might give it another shot and see what happens..


Cheers..!

---

### Post by red33m on 2009-09-03
What are you the God of Ubuntu???

The shot I took was deadly..! I installed Cinelerra..! and corrected the broken packages at the same time..!

Now I am gonna eat some musaka to celebrate(just kidding...!)

Thanks doc..!

---

