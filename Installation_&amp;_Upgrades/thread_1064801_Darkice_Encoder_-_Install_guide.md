---
title: "Darkice Encoder - Install guide?"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by Bluerooms on 2009-02-09
Hi

Im pretty much new to the world of ubuntu. 

I am trying to set up an internet radio station for my university, and having spoke to a number of other university stations i figured the best way to go about doing this would be to use the Darkice encoder software to send a stream to an Icecast sever. All based on linux.

So i downloaded the darkice.deb file. and i keep getting the message 

"Error: Dependancy is not satisfiable: libfaac0"

now this suggests to me that i need to install the libfaac libary. but when i try do so i once again get a similar message.

has anyone out there set up a station on ubuntu using this method?

and if you have could you please explain how to go about setting it up using the easiest method.

note: i've also downloaded the source files for a couple of libraries, but i cannot get my head around how to install these.


any help would be appreciated. :)

---

### Post by Partyboi2 on 2009-02-09
Open a terminal (Applications>Accessories>Terminal) and install darkice from the ubuntu repository by typing
```
sudo apt-get install darkice
```
This way will automatically installing the package and its dependencies.

---

