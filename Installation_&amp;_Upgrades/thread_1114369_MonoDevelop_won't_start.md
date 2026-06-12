---
title: "MonoDevelop won't start"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Scooby Doo on 2009-04-02
I upgraded to jaunty last week and then a couple of days later read that monodevelop 2.0 had been released. Tried to compile it but keep getting errors. Specifically:
```
./MonoDevelop.Components/MenuButton.cs(166,33): warning CS0109: The member `MonoDevelop.Components.MenuButton.UseMarkup' does not hide an inherited member. The new keyword is not required
./MonoDevelop.Components/MenuButton.cs(172,35): warning CS0109: The member `MonoDevelop.Components.MenuButton.Markup' does not hide an inherited member. The new keyword is not required
./MonoDevelop.Components/GladeWidgetExtract.cs(79,47): error CS0030: Cannot convert type `Gtk.Widget' to `Gtk.Window'
Compilation failed: 1 error(s), 2 warnings

```[LEFT]I'm doing the install from [http://monodevelop.com/Download](http://monodevelop.com/Download) and following all the instructions. Can anyone help?

On a relating matter, is there any way to add it to my sources list so it gets updated automatically?

Thanks for any help.



[/LEFT]

---

### Post by obstriegel on 2009-04-03
I have the same problem here...

I think it is a problem with the gtk-sharp-library. It uses the wrong version or something..

Any suggestions?

Edit: This issue is also discussed in [this thread]("http://art.ubuntuforums.org/showthread.php?t=980739").
There are pre-built deb packages for monodevelop on [http://www.getdeb.net/app/MonoDevelop](http://www.getdeb.net/app/MonoDevelop) but I want to figure it out myself.

As stated in the thread, a new version of gtk-sharp etc. has to be installed...


> **ahitchman said:**
> I hit this problem. 

Getting [http://ftp.novell.com/pub/mono/sources/gtk-sharp212/gtk-sharp-2.12.7.tar.bz2](http://ftp.novell.com/pub/mono/sources/gtk-sharp212/gtk-sharp-2.12.7.tar.bz2) fixed it. I also needed [http://ftp.novell.com/pub/mono/sources/gnome-sharp220/gnome-sharp-2.20.1.tar.bz2](http://ftp.novell.com/pub/mono/sources/gnome-sharp220/gnome-sharp-2.20.1.tar.bz2).

I've managed to make and install, but running fails with missing Addins. Installing [http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.4.zip](http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.4.zip) got MD running.

Regards,
Pascal

---

### Post by directhex on 2009-04-03
Jaunty ALREADY contains 2.0 Beta 2. Are you really so impatient?

---

### Post by days_of_ruin on 2009-04-07
> **directhex said:**
> Jaunty ALREADY contains 2.0 Beta 2. Are you really so impatient?

Does it work on an normal install of jaunty?
Because I have tried it in vbox and off live usb and always have problems with it. In vbox the vala plugin doesn't work and on live usb the whole
program gives an error on startup and then closes.

---

### Post by directhex on 2009-04-07
> **days_of_ruin said:**
> Does it work on an normal install of jaunty?
Because I have tried it in vbox and off live usb and always have problems with it. In vbox the vala plugin doesn't work and on live usb the whole
program gives an error on startup and then closes.

The Vala plugin hasn't been updated yet for 2.0 final. It's a development release, monodevelop is 7 different source packages.

As of this second, the monodevelop packages in Jaunty have the following versions:

monodevelop 2.0+dfsg-1
monodevelop-boo 2.0-1
monodevelop-java 2.0-1
monodevelop-database 2.0+dfsg-1
monodevelop-vala 1.9.3-0ubuntu1
monodevelop-debugger-mdb 1.9.3-0ubuntu1
monodevelop-debugger-gdb 1.9.3-0ubuntu1

Using mismatched versions is not supported at all. More recent packages have Conflicts: in place to prevent incompatible addins being installed.

If you're not using one of the obsolete addins, and the app is failing to run, then you might consider filing a bug.

---

### Post by directhex on 2009-04-08
> **directhex said:**
> The Vala plugin hasn't been updated yet for 2.0 final. It's a development release, monodevelop is 7 different source packages.

As of this second, the monodevelop packages in Jaunty have the following versions:

monodevelop 2.0+dfsg-1
monodevelop-boo 2.0-1
monodevelop-java 2.0-1
monodevelop-database 2.0+dfsg-1
monodevelop-vala 1.9.3-0ubuntu1
monodevelop-debugger-mdb 1.9.3-0ubuntu1
monodevelop-debugger-gdb 1.9.3-0ubuntu1

Using mismatched versions is not supported at all. More recent packages have Conflicts: in place to prevent incompatible addins being installed.

If you're not using one of the obsolete addins, and the app is failing to run, then you might consider filing a bug.

Remaining 2.0 addons uploaded

---

