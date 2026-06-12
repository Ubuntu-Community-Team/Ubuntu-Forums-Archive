---
title: "Logitech V450 and btnx or hidpoint"
date: 2010-11-12
forum: Hardware
---

### Post by Nobody202 on 2010-11-12
I'm trying to map scroll up and down to page up and down respectively so that a game (Rise of the Triad) will interpret the scrolling motion as pressing page up and down. With btnx, I can assign the keys to the mouse fine, but for some reason it doesn't work in the game; the game still interprets it as scroll up and down. So I've tried installing hidpoint, but during installation I get the error

Launching HIDPoint Installer
./hidpointsetup: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

After some browsing, I unsuccessfully tried two methods to solve the problem:
1. sudo ln -s /lib/libpng12.so.0 /lib/libpng.so.3
2. sudo apt-get install libpng3
(because it actually contains the libpng.so.3 file)
but neither course of action changes the error.
This led me to believe the hidpoint1-0.bin file is corrupt, but after re-downloading it to no avail, I have no idea what the problem is.

Other important info:
running Ubuntu 10.10 on a dell xps 1640, 64-bit dual core processor.

Thanks for your time, all help is appreciated.

---

### Post by Tirish Anau on 2011-02-03
You are not alone, I have the same problem I was even able to find the directory that was not being able to find. [Idea]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CB0QFjAB&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1487037&rct=j&q=.%2Fhidpointsetup%3A%20error%20while%20loading%20shared%20libraries%3A%20libpng.so.3%3A%20cannot%20open%20shared%20object%20file%3A%20No%20such%20file%20or%20directory&ei=Yn5LTdioKoXZgAfij-XvDw&usg=AFQjCNE1w3K1w5ysA5FwfA4AVLhX4cSy0w&sig2=bhlt81d3NOrl2mCiEpIhwA&cad=rja") However, this changed nothing as I received the same response.

---

