---
title: "Azureus/Vuze having problem starting or stopping"
date: 2008-07-17
forum: General Help
---

### Post by phyre-x on 2008-07-17
Hi, I'm having a bit of a strange problem with the latest Vuze at the minute. Running on ubuntu 8.04 and after my last set updates i've got the problem that vuze will only start if launched by firefox when i've downloaded a .torrent file. If i try to launch Vuze on its own i get as far as the messages

"Starting Azureus...
Suitable java version found [http://java](http://java) = 1.6.0_06
Configuring environment...
Java exec found in PATH. Verifying..."

looking at the system monitor a java process does start, when i kill this process vuze then loads up along with a new java process and everything seems to be alright. when i try to exit vuze the exit messages dont appear in the terminal so i kill the java process belonging to azureus and after which the exiting messages appear and then a java process is left idle. If i run vuze as root and do "sudo vuze" then it works straight away no problems.

I've unpacked and moved vuze to /opt/vuze and taken ownership of the folder and all files , output of java --version is

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

So i'm thinking its a java problem that i've got with the permissions since it works fine as root.

Thanks for any help or suggestions

---

