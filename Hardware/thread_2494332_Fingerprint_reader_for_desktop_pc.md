---
title: "Fingerprint reader for desktop pc"
date: 2024-01-12
forum: Hardware
---

### Post by makem2 on 2024-01-12
Is there such a USB reader for a desktop Ubuntu pc nowadays?

I note that laptops with built-in readers seem to be sorted now.

---

### Post by TheFu on 2024-01-12
Yes, but none are secure.  A 10 yr old can gain access if that is the only factor of authentication.  Rather, use a FIDO2 or smartcard device if you need 2FA.

It should go without saying, but unlocking phones using just a fingerprint isn't secure either.

Don't believe the "features" from these devices or the vendors behind them.  They seldom list any of the problems.  Here's an example, 
[https://arstechnica.com/security/2024/01/hackers-can-id-unique-apple-airdrop-users-chinese-authorities-claim-to-do-just-that/](https://arstechnica.com/security/2024/01/hackers-can-id-unique-apple-airdrop-users-chinese-authorities-claim-to-do-just-that/)

---

### Post by makem2 on 2024-01-13
> **TheFu said:**
> Yes, but none are secure.  A 10 yr old can gain access if that is the only factor of authentication.  Rather, use a FIDO2 or smartcard device if you need 2FA.

It should go without saying, but unlocking phones using just a fingerprint isn't secure either.

Don't believe the "features" from these devices or the vendors behind them.  They seldom list any of the problems.  Here's an example, 
[https://arstechnica.com/security/2024/01/hackers-can-id-unique-apple-airdrop-users-chinese-authorities-claim-to-do-just-that/](https://arstechnica.com/security/2024/01/hackers-can-id-unique-apple-airdrop-users-chinese-authorities-claim-to-do-just-that/)

I nearly missed your reply :(

You say, "[COLOR=#000000]It should go without saying, but unlocking phones using just a fingerprint isn't secure either." but banks allow that method. The alternative is to use a selection from your pass number. I bet 99.999..... people use their fingerprint because like I, I thought once 'tied' into the bank web page it was a secure method.

I gather that passkeys are being pushed now and I intend to take them up.[/COLOR]

---

### Post by TheFu on 2024-01-13
Banks aren't the best at security.  It is scary, if you ever get to look inside.  They are pretty clueless, but not as clueless as hospitals and doctor offices.

You should do different sorts of internet searches.  Stop looking for "how this works" and start looking for "how this can be easily broken".  That will open your eyes ... assuming those still work.

Just because something is used by nearly everyone, that doesn't make it secure.  Nearly everyone is really stupid about security.

When you were a teen, didn't your parents ask you, "if everyone jumped off a cliff, would you follow them?" to make the point that you and your peers all did something stupid?

---

### Post by Morbius1 on 2024-01-13
You mean something like a Yubikey BIO: [https://www.yubico.com/setup/yubikey-bio-series/](https://www.yubico.com/setup/yubikey-bio-series/)

---

### Post by makem2 on 2024-01-13
> **Morbius1 said:**
> You mean something like a Yubikey BIO: [https://www.yubico.com/setup/yubikey-bio-series/](https://www.yubico.com/setup/yubikey-bio-series/)

Yes I did but reading TheFu's input I think I will stick to using the keyboard. I note that it is Linux compatible though.

I have two laptops each with fingerprint sign-on but I have never used the readers with web pages such as banking. I'm not sure you can as I thought this was the realm of smart phones and **assumed** being connected using a smart phone to my bank and signing in using my finger instead of number selection was just as safe.

TheFu suggests that its not but surely this would have popped up in the wide world? I don't want to be a lemming but......

---

### Post by TheFu on 2024-01-13
> **makem2 said:**
> Yes I did but reading TheFu's input I think I will stick to using the keyboard. I note that it is Linux compatible though.

I have two laptops each with fingerprint sign-on but I have never used the readers with web pages such as banking. I'm not sure you can as I thought this was the realm of smart phones and **assumed** being connected using a smart phone to my bank and signing in using my finger instead of number selection was just as safe.

TheFu suggests that its not but surely this would have popped up in the wide world? I don't want to be a lemming but......

Security is about risk management.  Only you can decide if the risk is worth any convenience or not.

The idea that fingerprints are 100% unique has not been proven. In fact, there are people wrongly convicted based on incorrectly read fingerprint information. Only later, when it was proven they weren't even in the country where the crime was committed were they exonerated.

Fingerprint experts have built their career on the idea that fingerprints are unique and while statistically, it is very unlikely there will be matches.  Since their careers are built around this single idea, anything that confronts it will quickly become a problem for them and everyone else in that career path.  They don't like it.

The number of points are used on a print are how we typically decide how accurate any fingerprint comparison may be.  More points should equate to more accuracy. That intuitively makes sense.  Picking the right points matters.  Hardware devices that handle more points and are more consistent will cost more.  The software involved is seldom F/LOSS, if ever, so we never really know how the validation that a print read today matches one from last year.  There's a little too much smoke there to have a clear view.

The Apple iOS fingerprint is probably one of the best, outside FIPS standards.  In 2022, it wasn't so hard to crack it, but Apple has taken steps to make that less and less likely. The most effective step they took was limiting the number of attempts before a device is wiped.  Users probably need to enable that, since I doubt it is enabled by default.  If so, people would have their iOS devices wiped all the time by people either as a joke or nefariously - sorta a denial of service/device attack.

So we are left with devices that don't wipe the data and OS out there.  What, exactly, are you trying to protect? How important is it that it never be accessed by others?  Do you already have disk encryption enabled to prevent other, easier, ways for full access to the system?

Are you trying to keep a pre-teen off the system or are you trying to protect corporate or national secrets?  Those are very different risk factors and would feed into the choice for the amount of security that is reasonable.  Only you can decide.

I'd never use a body part that is easily removed for bio-metric security.  That just seems like a really bad idea to me.  OTOH, I have multiple keys, FIDO2, and even SecurID devices.  If someone takes those, I don't have to lose a finger.  These are for 2FA, never as a single factor.  They are the "something I have" part.  My brain and password manager have the "something I know" part.  A userid isn't "something I know", btw, though I do use random characters for userids at financial institutions.  I don't actually know the login name to my bank and wouldn't have any way to guess it.  Additionally, it uses a bank-only email address that is never used anywhere else, ever.

My personal bank provided me with a SecurID FOB for free. I just had to ask for it.  The codes for login change every 60 seconds.  Further, I only run it from a browser that appears to be freshly installed and stores nothing at all to any storage, not even temporary files.   It would be really bad if the company payroll were stolen from the corporate bank account, since liability is limited for banks with business accounts.  The national bank insurance only applies to consumer bank accounts and is limited to $500K.  While our company is small, everyone working there needs their paycheck and has a mortgage to pay, so I don't want to do anything foolish to risk their paychecks.

The corporate bank we use is using something as a 2nd factor that is trivial to get around - pure security theater.  I can't believe they have a straight face acting like their simple method provides any real security for the attacks in the wild today.  The security team at my company had a laugh about it.  We know some of the people working at that bank both in their IT security and in consumer banking.  They are all at "VP" level and above - at banks, a "VP" title is like a director at other large companies.  Anyway, their own IT security people know their fake security isn't useful, but upper management wanted to be seen as doing something. It is more about marketing than actual security.

Some people may think I'm overboard on security. If you have little to risk, perhaps that is fine.

---

