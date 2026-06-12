---
title: "Keyboard Hotkeys"
date: 2009-08-10
forum: Hardware
---

### Post by RED Lemming on 2009-08-10
Okay I know there has been a number of other threads about similar issues, but this is different.

I have a [Microsoft Natural Ergonomic 4000]("http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=043&active_tab=systemRequirements") it is a nice keyboard and I don't really want to chuck it, but I would like its full functionality back.

Especially the nice little app' that allows you to quickly reconfigure the hot-keys (1 - 5) by pressing one particular hot-key (favourites). I used to be able to get it to launch a program or even a simple bit of code and I kind of miss that.

I have looked through the keyboard shortcuts and have been unable to find the specific buttons that correspond to the reconfigurable hot-keys. And the layout is set to the closest one available on the layout list.

Could I write an app and bundle it with the keyboard configuration? if so what language would people recommend and could you point me in the right direction.... 

(preferably not the door :-))

---

### Post by IcarusR on 2009-08-10
I would suggest you google 'keyboard hotkeys linux' & do some reading. There is a lot of info around.

---

### Post by RED Lemming on 2009-08-10
I consider my wrist slapped :-( Yes I should of googled more thoroughly.

Please understand I am only just starting to play around with the underpinnings of Ubuntu (and as a result fully expect to make some quite spectacular errors) so as far as googling for answers go I am a little more hesitant just to plunge right in....

I suppose that is a bit daft really, it is all running off the same kernel so it should all behave itself.

Treat this thread as more of a request for advice from people with experience predominantly (I would guess) with *buntu and more specifically Ubuntu.

I am treating this as a learning exercise, but would prefer to avoid any random blundering around excessively complicated avenues if there are easier ways available.

From the initial google hits I have identified probable methodology for the code and the direction to head in there (Using the xev tool I have identified the events for the hotkeys :-) ), when I get to the point of requiring to wrap it in a GUI is there anything in particular I should bare in mind?

I was thinking of maybe trying to tie it in with the normal application launcher dialogue.

So you could activate a field with the mouse, press the key and that would fill that field in, the next field would launch the normal application launcher dialogue and bind that command to the key. 

Maybe on initial launch of the program it should ask for a key with which it should bind itself to launch....

What program would be most effective to develope this with? Is there anything in the way Ubuntu normally handles it's hardware mapping or I/O that I should be aware of and avoid fouling up?

Thank you for you patience.

---

### Post by wojox on 2009-08-10
I have a Logitech and I set it to Generic in the Layout and now my Media buttons and Volume and all those extras are read.

When I go to Keyboard Shortcuts they come up as XF86AudioRaiseVolume and such. You may want to try that.

---

