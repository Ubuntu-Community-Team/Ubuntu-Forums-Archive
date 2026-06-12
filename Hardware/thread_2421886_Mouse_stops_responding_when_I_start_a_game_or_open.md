---
title: "Mouse stops responding when I start a game or open steam and play a video in it"
date: 2019-06-28
forum: Hardware
---

### Post by darthdeus on 2019-06-28
Let me prefix this by saying that I only started experiencing the issue in the past month. I've used the same linux install early this year for months and everything worked fine, then switched off, came back a few months later, upgraded packages and did some more stuff (can't pinpoint exactly what), and then I started experiencing the issue.

The problem is, **when I open any game, or steam starts playing video (or probably anything GPU-accelerated) my mouse freezes, doesn't move, and doesn't respond to clicks**. The keyboard still works, so for example in steam I can move around with the keyboard, but the mouse doesn't work even if I switch to other programs. When I kill the process, the mouse starts working after a few seconds as if nothing happened.

What is interesting is that I also have CUDA installed, and running CUDA stuff does not cause this issue, and CUDA is using the same driver. I tried both the version of the driver packaged with CUDA, as well as installing it with apt, but both cause the same issue. I also think I used the exactly same driver few months ago when things worked, but I can't guarantee.

My setup:
- ubuntu 18.04
- nvidia 1080ti with the properietary driver 418.56
- mouse razer naga chroma

What I'm 99.99% sure is that it stopped working after upgrading things other than the driver, because I initially had both CUDA and the driver installed via a .run file and not via apt, and that only gets updated manually (AFAIK).

If it's of any relevance, here's the output from `xinput`

```
$ xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Naga Chroma                   id=8    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Naga Chroma                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard       id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Razer Razer Naga Chroma                   id=10   [slave  keyboard (3)]
    &#8627; Blue Microphones Yeti Stereo Microphone   id=11   [slave  keyboard (3)]
    &#8627; Yubico YubiKey OTP+FIDO+CCID              id=12   [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard       id=13   [slave  keyboard (3)]
    &#8627; Razer Razer Naga Chroma                   id=15   [slave  keyboard (3)]
    &#8627; Corsair Corsair Gaming K70 LUX RGB Keyboard       id=16   [slave  keyboard (3)]

```

I also watched dmesg -w, but nothing gets logged during the mouse freezing.

One reliable way of reproducing the issue other than steam I found is with Battle for Wesnoth (installed via `apt install wesnoth), so the issue is not only caused by steam games.

I guess part of the question is where else I should look for at least some log message regarding this, as journalctl also doesn't show anything.

---

### Post by Autodave on 2019-06-28
My very first thought was: did you try a wired mouse or another mouse?

---

### Post by darthdeus on 2019-06-28
> **Autodave said:**
> My very first thought was: did you try a wired mouse or another mouse?

I feel stupid for not having tried this, even though the first mouse is wired.

Turns out it is mouse related, because the second mouse keeps working even when the first one freezes. Why I find this a bit surprising is that I have dual boot with windows, and the "problematic" mouse works completely ok there, even in games.

Could it be that because it also has buttons on it that act as a keyboard it somehow gets captured incorrectly?

edit: I also tried changing the driver to 430.x, but didn't help.

---

### Post by CatKiller on 2019-06-28
> **darthdeus said:**
> Could it be that because it also has buttons on it that act as a keyboard it somehow gets captured incorrectly?

Other mice that also get picked up as keyboards are fine. It's more likely that your mouse does something else peculiar and no one knows about it, since Razer aren't interested in Linux and are interested in keeping whatever commercial advantage they may have confidential.

There has been work recently to make Logitech devices work properly by default, so maybe whatever thing your mouse was doing before it can't any more.

There are projects for documenting and making work random unsupported-by-the-manufacturer hardware. I'd imagine your mouse would have one of those already. Or you could try to fix it in mainline, if you have the commitment. Or just use the mouse that works for now.

---

### Post by darthdeus on 2019-10-04
> **CatKiller said:**
> There are projects for documenting and making work random unsupported-by-the-manufacturer hardware. I'd imagine your mouse would have one of those already. Or you could try to fix it in mainline, if you have the commitment. Or just use the mouse that works for now.

Thanks for the suggestions. I'd like to investigate this further, but I'm a bit lost as to what to try or where to look. Mostly because nothing shows up in dmesg/journalctl. I do have quite a bit of programming experience, but never contributed to Linux/Ubuntu, so not sure which direction to take. Would you please be able to provide a few pointers as to where to look, or what diagnostics tools to try, or even some resource to look at for how ****y hardware can cause issues?

---

### Post by CatKiller on 2019-10-04
> **darthdeus said:**
> Thanks for the suggestions. I'd like to investigate this further, but I'm a bit lost as to what to try or where to look. Mostly because nothing shows up in dmesg/journalctl. I do have quite a bit of programming experience, but never contributed to Linux/Ubuntu, so not sure which direction to take. Would you please be able to provide a few pointers as to where to look, or what diagnostics tools to try, or even some resource to look at for how ****y hardware can cause issues?

I'd suggest starting with having a chat with the [libratbag](https://github.com/libratbag/libratbag) people, who describe their project as 

> libratbag provides **ratbagd**, a DBus daemon to configure gaming mice. The daemon provides a generic way to access the various features exposed by these mice and abstracts away hardware-specific and kernel-specific quirks. 

There are hardware-specific projects, like [OpenRazer](https://openrazer.github.io/) but libratbag acts as a central location for a whole bunch of devices, with a nice configuration tool called piper, which makes it much easier for distros to include it and allows more people to benefit from the work.

Either of those projects should be able to tell you how you can best contribute and what information would be useful.

---

