---
title: "clustering question"
date: 2008-07-23
forum: General Help
---

### Post by malfist on 2008-07-23
I have a laptop and a desktop. Both function as two totally different computers. However, they're both almost always on, and I have a question.

My desktop has a quad core and it's really fast, but my laptop only has a slow dual core. How can I set up some form of clustering so that they can share processing power across a network?

For example, both computers are on the same subnet, so network latency isn't that much of an issue. I want to be able to send my desktop instructions from my laptop. (It is not necessary to send instructions from my desktop to laptop) But I still want to be able to use my desktop and laptop separately. My desktop is general purpose, and my laptop is running a webserver and some other stuff for web development. (desktop is mainly for games and application development)

Is this possible, does anyone know how to do this?

edit: Is this Ad-Hoc Clustering?

---

### Post by meatpan on 2008-07-23
Are you running completely different programs on each machine?  If so, why not open up a session on the desktop (from your laptop via ssh), and run the more compute intensive apps from that terminal?

---

### Post by malfist on 2008-07-23
I am running seperate programs. I haven't set up SSH because I would like something that would be semi-seamless. For example, firefox consumes too much reasources (memory and cpu), if both computers can share the load it would work a lot better. However, ssh would also solve that issue, but not as seamlessly. I don't want to have to say, run firefox here, run apache here, etc. You see what I mean?

Thanks for the idea though, I hadn't thought of it.

---

