---
title: "Jaunty and Compiz on the x3100"
date: 2009-04-30
forum: Hardware
---

### Post by stchman on 2009-04-30
Hello all, I am wanting to upgrade my laptop from Hardy to Jaunty.  I will be going the clean install route.

I downloaded the .iso and created a bootable USB drive.

After loading up Jaunty it appears that Compiz does not function on Jaunty under the x3100.  After doing some reading there appears to be a bug in the xserver-xorg-video-intel package.  It appears that the driver is blasklisted.  Now I have an Aspire One which uses the i945 and Compiz works prefectly.  The x3100 is i965.

My question is there a workaround?  Will the package be fixed?

Thanks.

---

### Post by zevans on 2009-05-01
> **stchman said:**
> Hello all, I am wanting to upgrade my laptop from Hardy to Jaunty.  I will be going the clean install route.

I downloaded the .iso and created a bootable USB drive.

After loading up Jaunty it appears that Compiz does not function on Jaunty under the x3100.  After doing some reading there appears to be a bug in the xserver-xorg-video-intel package.  It appears that the driver is blasklisted.  Now I have an Aspire One which uses the i945 and Compiz works prefectly.  The x3100 is i965.

My question is there a workaround?  Will the package be fixed?

Thanks.

A fix is about to be released to Jaunty-proposed, after EPIC discussion on the launchpad bug. The fixed package is being built now. I don't know how long things take to make it from -proposed to -updates, guess we've got to leave some time to check there are no regressions and that it really does fix the issue.

You could try adding -proposed to your repo if you're happy with the bleeding edge, but me, I'd just put up with it and wait for the official tested fix, since it's already been identified.

---

