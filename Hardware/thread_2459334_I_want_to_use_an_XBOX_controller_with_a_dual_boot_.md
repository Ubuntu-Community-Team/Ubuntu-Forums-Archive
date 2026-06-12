---
title: "I want to use an XBOX controller with a dual boot linux/windows machine"
date: 2021-03-16
forum: Hardware
---

### Post by makem2 on 2021-03-16
I would like to use a controller for minecraft instead of keyboard buttons and mouse due to finger problems.

Can anyone suggest which wifi (preferably) controller would work 'out of the box' with 20.04?

Failing on the 'out of the box' part, how about a working guide to get it working as I have done some research during which I found lots of different help which may of may not work.

---

### Post by Tadaen_Sylvermane on 2021-03-16
Its all about how hard it is to map keys. If you can map the. The. The sky is the limit.

---

### Post by CatKiller on 2021-03-16
You probably mean Bluetooth rather than WiFi.

More controllers work than don't. I've used a DualShock 3 and a Steam controller with no problems, and I understand that the DS4, DualSense, Logitech controllers and 8bitdo controllers all work fine. I believe that one model of Xbox controller is particularly finicky and needs extra software, but I can't remember which one since it's not something I have any interest in using.

The easiest way to use a controller for Minecraft is to add it as a non-Steam game to Steam. Big Picture Mode works best. Then you can use Steam's own controller support and control remapping to set it all up how you want.

---

### Post by makem2 on 2021-03-16
> **CatKiller said:**
> You probably mean Bluetooth rather than WiFi.

More controllers work than don't. I've used a DualShock 3 and a Steam controller with no problems, and I understand that the DS4, DualSense, Logitech controllers and 8bitdo controllers all work fine. I believe that one model of Xbox controller is particularly finicky and needs extra software, but I can't remember which one since it's not something I have any interest in using.

The easiest way to use a controller for Minecraft is to add it as a non-Steam game to Steam. Big Picture Mode works best. Then you can use Steam's own controller support and control remapping to set it all up how you want.

That sound good. 'Big Picture Mode'? A steam setting?

Yes, testing controllers would be expensive.

I did actually mean wifi rather than bluetooth thinking that I had seen them on amazon.

---

### Post by CatKiller on 2021-03-17
> **makem2 said:**
> That sound good. 'Big Picture Mode'? A steam setting?

Yes. It's the Steam interface designed for using at a distance with a controller.

I've remembered another quirk of using Minecraft in Steam for the controller support: you need to set it so that the launcher stays open. As far as Steam is concerned, it's the launcher that you wanted to run, so that's what it sends the controller inputs to. If the launcher closes when you launch the game then Steam doesn't know to send the inputs to the game instead.

---

### Post by makem2 on 2021-03-17
> **CatKiller said:**
> Yes. It's the Steam interface designed for using at a distance with a controller.

I've remembered another quirk of using Minecraft in Steam for the controller support: you need to set it so that the launcher stays open. As far as Steam is concerned, it's the launcher that you wanted to run, so that's what it sends the controller inputs to. If the launcher closes when you launch the game then Steam doesn't know to send the inputs to the game instead.

Thank you for your input.

---

### Post by mastablasta on 2021-03-18
when searchign for controller you might want to check what is selling on sites that sell raspbery pi. they are pretested and usually work out of the box with linux. i found (searching for best linux controlers)  that some xbox controllers and controllers made for xbox and PS4 work well. i was reading up on it as well as i was thinking of using my current old machine as old games machine.  there are a couple of reviews out there and you can check them out. Some slightly cheaper "ocpies" provide good quality and experience.

---

### Post by makem2 on 2021-03-18
Well, I borrowed an xbox one controller and got it paired via Bluetooth. However it cannot connect giving an Input/output error.

The Big Picture mode says no device connected.

Using a usb connectionI  can raise the Big Picture mode and change setting although I left at default.

My problem now is to somehow tell minecraft to use the controller via steam. Cannot figure out how to do that.

I was under the impression that if MC was opened via steam then steam control settings worked without any changes in MC.

Edit: Forgot to mention that using usb I can change setting in Big Picture mode using the controller.

---

### Post by CatKiller on 2021-03-18
> **makem2 said:**
> My problem now is to somehow tell minecraft to use the controller via steam. Cannot figure out how to do that.

There's a page in the per-game Steam configuration that says what you want each button to do. Tell it that you want the buttons to give keypresses and mouseclicks and whatever. Minecraft doesn't need to know that you're using a controller.

---

### Post by makem2 on 2021-03-18
Well this IS disappointing!

I borrowed another Xbox One controller and was able to pair and connect. Able to use it in Big Picture mode, but, still cant figure out how to tell minecraft to use the controller!

---

### Post by makem2 on 2021-03-18
> **CatKiller said:**
> There's a page in the per-game Steam configuration that says what you want each button to do. Tell it that you want the buttons to give keypresses and mouseclicks and whatever. Minecraft doesn't need to know that you're using a controller.

Posted my previous result before seeing this reply thanks.

I have been looking for such but never saw a page which actually gave a key choice. Now I know there is such a page I will try to find it. Thanks again

---

### Post by CatKiller on 2021-03-18
You can download pre-made profiles (from Steam or community members) that can be a good starting point. I expect that "mouse and keyboard" is a pre-existing default profile.

I'm typing from my phone, which is why I haven't just told you what the option is called: I'm not at my computer to remind myself.

---

### Post by makem2 on 2021-03-18
> **CatKiller said:**
> You can download pre-made profiles (from Steam or community members) that can be a good starting point. I expect that "mouse and keyboard" is a pre-existing default profile.

I'm typing from my phone, which is why I haven't just told you what the option is called: I'm not at my computer to remind myself.

Ok thank for hanging in with me.

I found out how to change the up, down, left. right keys to the controller but it still didn't work in MC.

You have to keep selecting legacy keys to get the key choices for each move. So I make some progress but still need to connect the controller to MC lol.

I will investigate pre-configured profiles thanks, there maybe some help within there.

---

### Post by CatKiller on 2021-03-18
You'd set the buttons to, like, W A S D, or whatever movement controls you're using in Minecraft. Then when you press the buttons Minecraft gets a W or whatever, and moves you forward.

Edit: I've just checked it in Steam, and you find the game in your BPM library and select Controller Configuration. If you "browse configs" then one of the templates is "Keyboard (WASD) and Mouse." That would make a good starting point, but you can change it up however you want.

---

### Post by makem2 on 2021-03-18
> **CatKiller said:**
> You'd set the buttons to, like, W A S D, or whatever movement controls you're using in Minecraft. Then when you press the buttons Minecraft gets a W or whatever, and moves you forward.

Edit: I've just checked it in Steam, and you find the game in your BPM library and select Controller Configuration. If you "browse configs" then one of the templates is "Keyboard (WASD) and Mouse." That would make a good starting point, but you can change it up however you want.

I find the game MC in BPM library and select controller configuration.

When I do this it says controller configuration is disabled. You must enable Xbox controller in main steam controller configuration and then enable it in controller configuration!

I will try but its seems rather convoluted. Still, can't give up lol.

---

### Post by CatKiller on 2021-03-18
> **makem2 said:**
> When I do this it says controller configuration is disabled. You must enable Xbox controller in main steam controller configuration and then enable it in controller configuration!

So... do that.

It's just a tick box to say that you want to use the Steam controller configuration tool for different classes of controller.

---

### Post by makem2 on 2021-03-18
I did finally get it to work :D

However, the pre-configs are not suitable but were a good guide to start with. Eg. I could fly up but couldn't fly down lol.

I did find it was very responsive and may in fact be too responsive. Need to practice to get the hang of it obviously.

I had 3 different controllers which were 'throw-outs' from the kids who are onto better things lol

The one which worked with Bluetooth had a mind of its own and was difficult to get it to do what you wanted, one, a wired one, I didn't have a wire for (strange connection), the other didn't work with Bluetooth. So I was lucky to get one working although flaky.

I will practice with that for a while before deciding to buy and use a controller or go back to the keyboard which is certainly more accurate.

I thank you for you patience and help.

---

### Post by makem2 on 2021-03-18
> **mastablasta said:**
> when searchign for controller you might want to check what is selling on sites that sell raspbery pi. they are pretested and usually work out of the box with linux. i found (searching for best linux controlers)  that some xbox controllers and controllers made for xbox and PS4 work well. i was reading up on it as well as i was thinking of using my current old machine as old games machine.  there are a couple of reviews out there and you can check them out. Some slightly cheaper "ocpies" provide good quality and experience.

That you for that info. I do have a couple of Pi's used with SSD's for backups and torrents.

Your suggestion for finding a working controller is a good idea and I will follow it up.

---

### Post by CatKiller on 2021-03-18
> **makem2 said:**
> I did find it was very responsive and may in fact be too responsive. Need to practice to get the hang of it obviously.
The Steam controller configuration screen will let you fiddle with things like sensitivity and deadzone, which might make things more comfortable for you.

I use a Steam controller (which has a trackpad) for mouse-like games when I don't want to use a mouse - because I'm playing on a telly or a laptop, for example - and the PS3 controller when I'm using controller-like games.

Edit: If you bring up the Steam overlay while you're in-game (Shift-Tab, or a controller's "Home" button) you can change the controller settings from there so you can tweak things quickly.

---

### Post by makem2 on 2021-03-18
For anyone who may follow I found this to be a very good button mapping tutorial.

[https://www.youtube.com/watch?v=Ze7MyUrDNKs](https://www.youtube.com/watch?v=Ze7MyUrDNKs)

Only thing I need to add is an ability to fly down as I have a flight ability and by double clicking the space bar then holding it down I can fly up.

I use Left shift on the laptop keyboard so need to map that somewhere or use an alternative as I also use Left shift for 'sneak'

What button to choose???

If anyone has a good suggestion please add it.

---

