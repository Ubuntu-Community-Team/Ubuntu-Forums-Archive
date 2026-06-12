---
title: "Ubuntu Caused BIOS to crash?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by radopod on 2009-08-18
Hi there
I recently did a clean install of Ubuntu on one of my Professor's laptop. She is interested in Open Source technologies so I decided to help by installing Ubuntu on her system. The Laptop on which the installation was done is a [Toshiba Satellite 2400]("http://www.google.co.in/search?q=Toshiba+Satellite+2400&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") which has been running absolutely fine for the pass 6 years with zero problems to date.

I decided to first show her how the OS feels by using the 'Test it out' feature of the Live CD and once she confirmed that she liked it, I decided to go ahead with the format and installation.

The install went perfectly fine and the system rebooted nicely for about 3 times as I tried to set a few settings right.

After about the third restart the BIOS of the system went haywire and the following confirmed that;

> [Block 1] error. Kindly contact your Serviceman.
Serviceman: Kindly insert your maintenance disk.

I had never seen something like this. My Professor has since then shown the system to the Toshiba Service center and they suspect that Ubuntu has a role to play in this. They have suggested that they will try and reflash the BIOS. If that doesn't work, replacing the BIOS chip seems the only option.

I am really shocked to see that Ubuntu is not compatible with laptops that are 6 years old! I would like to have a discussion on it and know if whether Ubuntu really has problems with such systems? I have searched for similar issues on Launch Pad and the forums here but they have turned up with nothing. It is kind of contrary of what I know of Ubuntu as people I know have installed it on really old systems(Desktops) and seem to be happily using them.

The Service Center people have suggested that we install Windows XP on it.

---

### Post by Revolutionary101 on 2009-08-18
I doubt that is was caused by Ubuntu and to me it just seems like the hardware failed. If it booted three times with no problems then it points to the fact that Ubuntu did not play a role in making the BIOS crash (or maybe it could have been you tweaking the settings). If it was Ubuntu's fault it would have crashed the first time you tried to reboot it. Also the only reason the Service guys said to reinstall XP on it is because if it breaks they are more familiar with Windows so it will be easier for them to fix it.

---

### Post by radopod on 2009-08-18
I do remember one particular thing though. There was an issue when we tried to put it to sleep and when it refused to do so, we were forced to open it and(the screen had gone blank) and force shut down it using the Power button. Could this be the cause of the issue?

---

### Post by Revolutionary101 on 2009-08-18
> **radopod said:**
> I do remember one particular thing though. There was an issue when we tried to put it to sleep and when it refused to do so, we were forced to open it and(the screen had gone blank) and force shut down it using the Power button. Could this be the cause of the issue?

Maybe, but I have had to force shut down my laptop numerous times and the BIOS is still working perfectly.

---

### Post by radopod on 2009-08-18
Agreed! I have done that close to infinite times to my system as well and it has never failed. The only failure that I have had on older systems i.e. Desktops on doing this is that the Windows Installation has crashed but is a HD error as we all know. I am still looking in what could have possibly caused this kind of an issue. Was it a coincidence that the Installation of Ubuntu coincided with the BIOS failure?

---

### Post by Revolutionary101 on 2009-08-18
> **radopod said:**
> Agreed! I have done that close to infinite times to my system as well and it has never failed. The only failure that I have had on older systems i.e. Desktops on doing this is that the Windows Installation has crashed but is a HD error as we all know. I am still looking in what could have possibly caused this kind of an issue. Was it a coincidence that the Installation of Ubuntu coincided with the BIOS failure?

I think it was just a coincidence. I think if your professor had Windows on it the same thing would have happened.

---

### Post by Mark Phelps on 2009-08-18
When you installed Ubuntu, you said you did a clean install.  In that case, did you first wipe out the XP installation? If so, did you also wipe out any hidden partitions?

I'm asking this because if the Toshiba laptop came with XP preloaded, then is most probably used a BIOS-locked activation scheme for XP (known a using a SLIC table).

While Ubuntu doesn't know, or care about, that scheme, since laptop BIOS's are customized by the OEMs, there's a remote possibility that the BIOS looks for something related to XP when it boots.  If it did that EVERY time, you should have received the error message on the first Ubuntu boot. If it's programmed to only do that every few boots, that could explain why it is complaining now.

You could try booting a few more times to see if it continued to complain on every boot.

But, AFAIK, Ubuntu does nothing to tamper with the BIOS, either during installation, or during machine boot.

---

