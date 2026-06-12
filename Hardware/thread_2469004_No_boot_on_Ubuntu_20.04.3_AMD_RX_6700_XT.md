---
title: "No boot on Ubuntu 20.04.3 AMD RX 6700 XT"
date: 2021-11-16
forum: Hardware
---

### Post by jerome1232 on 2021-11-16
Hello! I'm having issues installing Ubuntu, when I boot the USB I have to either boot in safe graphics mode, or edit the boot line and add "nomodeset" or it just sits at a blank screen.

Once the OS is installed I have the same issue with the install, I tried installing amdgpu from AMD's site, and it's installer fails when trying to build the dkms module. I'm a bit baffled because as far as I understand, amdgpu driver should be built into 5.11 kernel right?

What is it that I'm doing wrong here? (I've only ever dealt with Nvidia cards before, AMD is a new territory for me)

AMD Ryzen 7 5800x
AMD RX 6700 XT
Dell Alienware Aurora R10

---

### Post by DuckHook on 2021-11-16
I had a similar problem with my video card, it too being an AMD RX 6700 XT. The problem is that this video card is too brand spanking new and bleeding edge. The drivers included in the 20.04 kernel are not sufficiently updated to run the card.

I have three OS partitions on my main machine. I was luckier than you in that I was at least able to get a working desktop. However, it was a brutal 1024x768 resolution on a 4K monitor. Eeeew.

The following were my experiences:

[list=1]
[*]On my main partition, I could never get the AMD supplied driver to work at all. It wouldn't build because of dependency conflicts with something else that I never bothered to chase down and identify. I had to install the amdgpu-pro driver *from the repos*, not the one from the AMD site. This one doesn't work as well as the AMD site driver, but it does work.
[*]The AMD site driver is 32 bit (another Eeeew). It did install after much tweaking and configuring, but only into my second OS partition. I had to enable 32-bit architecture support first. I have no idea why it installs in my second OS but not my first. They both run Focal. Perhaps the conflict is in some other service like WINE or my VM. Whatever the reason, it is arcane and obscure.
[*]The drivers on the AMD site are a dog's breakfast, with outdated, updated, old and new all jumbled together. Very hard to figure out the proper one. I had success with: amdgpu-pro-21.30-1290604-ubuntu-20.04.
[*]My third OS partition proved to be the best/easiest solution. This is the partition I use for testing/playing, so it has 21.10 on it. I'm happy to report that your/my video card runs like a charm on Impish. It is not only native, but runs faster, leaner and cleaner than the AMD issued driver in Focal. If you are willing to upgrade to a standard release, hopefully, you will only need to wait a few months for Jammy to go back to LTS. I suppose that we can be pretty sure Jammy will support your card given that Impish already does.
[/list]

---

### Post by jerome1232 on 2021-11-16
I noticed that about AMD's site, I realized I was originally trying with outdated drivers!

I did end up trying 21.10, works like a charm, out of the box like you said (yay!). No OpenCl however. I managed to bork everything trying to get OpenCl working, couldn't get it back to the "just working like magic" state it started out in. I'm currently in the middle of wiping and retrying. I may go back to 20.04 and trying again with that, I do like being on LTS, and I need OpenCl working.

---

### Post by DuckHook on 2021-11-17
I'm afraid I'm out of my depth with OpenCL. I recall this being an option in the AMD version of amdgpu-pro, but since I don't need it, I've never explored it. What I do know is that my more pristine version of Focal was able to build the amdgpu-pro driver, so you might want to experiment with installing on such a partition.

---

### Post by jerome1232 on 2021-11-19
I've had some success!

On Ubuntu 21.10 Running kernel 5.13, with the built in amdgpu driver working I got opencl also working with a few steps.

1. Adding my user to the render group.
```
sudo usermod -a -G render $LOGNAME
```
2. Downloading the lastest AMD Radeon driver (as of 11/19/21 it's 21.40.1) from [here]("https://www.amd.com/en/support/graphics/amd-radeon-6000-series/amd-radeon-6700-series/amd-radeon-rx-6700-xt")
3. Installing their .deb (it seems to really just add a fancy script to your path and add their repos.
```
sudo apt-get install ~/Downloads/amdgpu-install_21.40.1.40501-1_all.deb
```
4. Running the newly added script to install the opencl stack, with no dkms
```
amdgpu-install --usecase=opencl --no-dkms
```
5. Enjoy!
6. Untested, installing anything else, I don't feel like borking this installation atm.

---

