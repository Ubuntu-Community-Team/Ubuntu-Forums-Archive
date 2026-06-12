---
title: "apt-get package suggestion when typing in cmd line"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by mohammadthalif on 2009-05-15
Hi all,

When I type a wrong command the apt-get match's a the package and suggest for installation. how this is done. can any one explain me.

for example.

$pi
The program 'pi' is currently not installed.  You can install it by typing:
sudo apt-get install pi

Thanks  ):P

---

### Post by lindsay7 on 2009-05-15
I am not sure what you are asking, it you want to install a program using the terminal you type  


sudo apt-get install pi if pi is the program name

the terminal will ask for your password, type that in, you will not see what you type, just hit enter.

---

### Post by mohammadthalif on 2009-05-15
hi lindsay7 

I know to install in the command line using apt get.

My qurrey is that. when I type a command in the command line pi it automaticaly matches the package  and return the suggestion like 

[I]The program 'pi' is currently not installed. You can install it by typing:
sudo apt-get install pi
[/I]

how this is achived. Do I need to configure apt get to report like that. If you see in debian apt-get is there but when i enter pi or any command it is not suggestion like done in the ubuntu. I want to configure debian too like ubuntu does

Thanks

---

### Post by lncoll on 2009-05-15
This feature is done by the **command-not-found** package, this is all that I know about.
You can look in Synaptic what files does this package install, there is a README file and some doc.

---

### Post by mohammadthalif on 2009-05-15
Thanks lncoll

This is what I was looking for.

---

