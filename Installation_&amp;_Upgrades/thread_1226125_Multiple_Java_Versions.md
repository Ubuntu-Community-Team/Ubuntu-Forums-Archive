---
title: "Multiple Java Versions"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by zamaddog on 2009-07-29
Hi all,

I am not sure whether this is under the right Forum. I also did search the Forums but only got incomplete answers to my problem.

I installed multiple versions of the SUN JRE (Version 5 & 6) on my Notebook on Netbook Remix. Have a critical application that only runs under version 1.4 or 1.5 of JRE (e.g. Java 5). Recently started working a bit with Proxmox virtualisation that is utilising Java for the VNC viewer to gain console access to the virtual machines.

JRE 1.5 works for the Proxmox but only on *nix VM's. The M$ VM's need 1.6 or Java 6 JRE to function properly. I need to get both versions running simultaneously and be able to tell the seperate applications to only use it's own version of Java.

So I am a bit stuck, tried to influence it in the various Applet Setup tools, to no avail.

---

### Post by Mighty_Joe on 2009-07-29
I use scripts to start my version-dependent Java applications.  Setting the JAVA_HOME environment variable to point to a particular version and setting the PATH to include that version of Java and whatever the application needs should be enough.
If you're uncomfortable with the command-line, you can create a launcher to run the script once it's working.

---

### Post by zamaddog on 2009-07-29
Thanks Mighty_Joe for the prompt reply. The problem I am stuck with is that both of these applications are called out of integrated Web Pages.

I tried the most important one to start it alone from the applet, but it relies on the browser to pass login and security credentials in order for it to run. BTW, this "little" applet is 30Mb download, so every time the JRE is wrong, it will try to "refresh" the applet. BUMMER :lolflag:

The VNC version of the applet is the same story, once you are authenticated in the Proxmox environment, then you can start VNC sessions. Else it just hangs around waiting for something.

> **Mighty_Joe said:**
> I use scripts to start my version-dependent Java applications.  Setting the JAVA_HOME environment variable to point to a particular version and setting the PATH to include that version of Java and whatever the application needs should be enough.
If you're uncomfortable with the command-line, you can create a launcher to run the script once it's working.

Maybe I should have "two versions of Firefox" starting each one with it's own Java credentials? Would that be possible? Any help on this appreciated.

---

### Post by Mighty_Joe on 2009-07-30
The JDK (as opposed to the JRE) has an tool called [appletviewer]("http://java.sun.com/j2se/1.5.0/docs/tooldocs/windows/appletviewer.html").  It's intended for testing applets when one is developing.  Maybe you could create a launcher that uses the appletviewer of the correct Java version to start your applet.

---

### Post by zamaddog on 2009-07-30
Hi Joe,

Got it right!. Did an install of both Java 5 and 6 version from Sun. Went to each of the Java Control Applets and let it search for all the different Java versions in /usr/lib/jvm/

It found multiple entries for 1.5 for instance, and added all of them. Now all of a sudden it all works properly :D , the 1.5 (Java 5) applet and the Java 6 applet. So it seems the key is to tell Java 6 (the system default) of all the different versions of JRE (the user default) that exists on the system. I can document and screen capture it if somebody is interested, just PM me. 

> **Mighty_Joe said:**
> The JDK (as opposed to the JRE) has a tool called [appletviewer]("http://java.sun.com/j2se/1.5.0/docs/tooldocs/windows/appletviewer.html").  It's intended for testing applets when one is developing.  Maybe you could create a launcher that uses the appletviewer of the correct Java version to start your applet.

---

