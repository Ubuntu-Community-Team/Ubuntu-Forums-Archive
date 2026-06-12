---
title: "Konqueror not browsing web pages"
date: 2008-07-21
forum: General Help
---

### Post by caseywise on 2008-07-21
I know this has to be a configuration issue but I've spent hours and hours on this and can't find the answer.

This is how it goes: 

1. I fire up Konqueror
2. In the address bar, I enter: "www.google.com"
3. I click on the "Gmail" link, this is what I get:

Open 'https://www.google...ltmplcache=2&hl=en'?
Type: HTML Document

With the following buttons below:

"Save As...", "Open with 'Kate'" & "Cancel"

Here's a screen cap of it.
[IMG]http://caseywise.com/konquerorError.jpg[/IMG]

I want it to browse to that Gmail page or whatever link I click.  Any help?

---

### Post by hal8000 on 2008-07-21
I just tried posting from Debian Lenny, and I was surprised that my konqueror (3.5.9 using KDE 3.5.9) behaves exactly the same way.

Not sure if youre using Ubuntu or Kunbutu, but heres how i fixed mine,
hopefully it will work for you.

Start konqueror, then from the menu bar choose settings, configure konqueror.
Click the icon for file associations, then type  "html" without the quotes on the find filename pattern. Click the + box next to text, then html.

You will see a list of apps in application preference order. Click on konqueror, then use move up button until it gets to the top of the list.
Click apply, ok and restart konqueror.

Now konqueror should work as a browser again.
Hope that helps

---

### Post by caseywise on 2008-07-21
hal8000, Thank you so much!  That got it.  Didn't know to poke around there.

I'm usuing Ubuntu 8.04 and frequently use of the KDE apps.

...and the learning continues!

Kind Regards,
Casey Wise

---

