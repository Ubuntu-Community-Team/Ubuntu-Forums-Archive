---
title: "Installing WICD [Use to work, now not so much]"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2009-09-29
Something to make you go hmmm!!!!

For the record I have done this on 3 laptops, latest one 2 months ago, now can't get is to work. :confused:

I have the WICD network manager DEB on a USB thumb drive for those times that I am installing Linux on a new laptop, all of which has been Kubuntu. I install WICD because no offence but the network-manager for Kubuntu is less than ideal for wireless communication on a laptop.

So I usually have my bag of tricks when it come to installing Linux on a new system in the form of a USB key. I have used it to set up 3 laptops in the past year, it has the ISO file of Distro and a partition for any DEBs I need, mainly WICD so I can get the network running then I can install the others off the net.

Recently I bought a 500gig hard drive for one of the computes I had work on before, and was getting ready to do a transplant. I miss placed the USB key so I simply download another copy of the ISO 9.04, the same version as the USB, and copied the same WICD deb file that I keep on my laptop for those rare occasion you need a backup.

So to stress again same version and file of the ISO and DEB file that I have used 3 times before.

Transplanted the hard drive, installed the Kubuntu, went to install the DEB file, now for some reason, I am missing dependencies. WTF!!! Never had that problem before. It alway installed straight. So I track down ALL the dependencies, and there were ALOT, and got it all installed, or at least I thought. Did a:
```

sudo apt-get remove network-manager

```...because the two would conflict, and as I had also learned 3 install ago, again a proceedure i was quite use to by now. Restart the computer... and nothing.

Copied over the wpa-supplicant file that I use as a template and modified it. Did a:
```

sudo /etc/init.d/wicd start

```... get the big OK, still nothing. Double check [http://wicd.net/download.php](http://wicd.net/download.php), everything seems in order.

So I am out of ideas as to what could be the problem. Like I said, done this before with no problems, all of a sudden I need dependencies, and not getting a connection or and icon on my desktop. Get nothing actually, not even able to configure WICD. It is kind of similar to when the first time I tried all this and did not know to remove network-manager, it just seems to lag there.

Any suggestions would be great.

I am :confused:

---

### Post by Tux Aubrey on 2009-09-29
A mystery indeed!

I'm puzzled by the fact that you are using the same versions as you previously installed successfully.

I have noticed that my most recent installs of wicd (from current Karmic repos) bring up a screen during the install asking me which user/s should be allowed to use wicd.  This didn't used to happen (as far as I can remember).

It might be worth checking to see whether there is a user/group permission problem now or try running wicd as root.

Just a thought.  Good luck.

---

### Post by p2bc on 2009-09-29
I don't know about WICD asking for a group, but I do have a group setup in my wpa_supplicant.conf file.

/etc/wpa_supplicant.conf
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/examples/README.wpa_supplicant.conf.gz
#  for more complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
#  specific configuration examples.

# allow frontend (e.g., wpa_cli) to be used by all users in 'WIFI' group
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=WIFI
#
# home network; allow all valid ciphers
network={
        ssid="Server"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="*******************************************************"
        proto=WPA
        key_mgmt=WPA-PSK
}

```In this case user part of the "WIFI" group can access the wireless internet.

---

### Post by p2bc on 2009-10-02
Well I have some more developments regarding this little problems, and a lot more ????

I tried again:
```

sudo /etc/init.d/wicd start
Starting wicd                        [failed]

wicd-client
Segmentation fault
wicd-client -n
Segmentation fault

```So I figured to re-install the DEB package. I ran it from the GUI, and it came back done, OK, no errors. But I figured to check the details for fun, and this is what I got:
```

(Reading database ... 89850 files and directories currently installed.)
Preparing to replace wicd 1.5.9 (using .../disk/Linux/wicd_1.5.9_all.deb) ...
   * Stopping Network connection manager wicd   ...done.

Unpacking replacement wicd ...

Setting up wicd (1.5.9) ...
ls: cannot access /opt/wicd/encryption/configurations/: No such file or directory
   * Starting Network connection manager wicd   ...fail!

Processing triggers for man-db ...

```Ok, I don't like seeing 4 failed in one sitting I have to admit, even if they are related. Errors are one thing, you did something wrong, here is where it is broken, failed is just a slap in the face. My 2 cents

Anyways I am spiraling in the sea of WTF, I never had these problems before and it is getting to me.

And to make things worst, and you have no idea how this irks me, Windows installed with little problems, actually the both "installed" no problem, getting Windows on the web was just a matter on installing a AntiVirus, and Firewall, and all 66 updates/patches and 1 Service Pack, which took a ridiculous 2 hours, but still shorter than this particular problem. Which is going on a week.

---

### Post by p2bc on 2009-10-05
No one has any ideas, none?!?

Pretty please, something I might have over looked, something.

I am resorting to begging here,... Ok that past   :-)

Anyways seriously, anyone with a suggestion.

---

### Post by p2bc on 2009-10-11
Ok this problem has been "resolved" not fixed, but resolved. I got wicd installed after down grading the network security step by step until I reach to absolutely not protection what so ever and was able to connect to the internet with network-manager, wireless and wired, bloody sad. I really hate the native network-manager.

Now a few points of interest that start to shed light on what was happening, but unfortunately does not answer a bloody thing.

So after finally connecting to the internet I did:
```

sudo apt-get install wicd

```It did its thing and was installed. I double checked the version of the wicd that was installed. It said is was version 1.5.9. I check the DEB file that I had, and it said it was version 1.5.9, so I decided to run a little test knowing there would be only 2 possible outcomes but expecting my suspicions will be confirm. The worst that would happen that it would re-install, so I proceeded to re-install the DEB file and low and behold I get what I figure, and error message the says," A newer version is already installed."  ???  So 1.5.9 != 1.5.9, interesting as I figured, and not to mention 9.04 downloaded in May != 9.04 downloaded in Sept. 

This is starting to turn into a rant so I will scale it back. Trying to keep this informative for those that stumble on this thread and have the same issues.

A recent build of a distribution might have slight changed that might have packages that are included or removed from what you previously expected. Which will lead to weeks of frustration. There is a naming convention that is in place that is left to the individual to uphold by appending increments to there versions to notify other individuals that there is a change no matter how slight, example 1.5.9**.1** So that as a person trying to use said packages are at least aware that there is a change, and maybe find documentation on said change.

I will leave it here, but please feel free to comment if you have and positive or negative ideas or comments, agree or disagree, whichever.

---

