---
title: "Help Help Help Help Help !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! !!!!!!"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by God.Jr on 2006-12-24
Plz Help I Put My Usb In My Port Yesterday And Now My Pc Won't Pic Up My Mouse

At The Moment I Am Using A Wacom Tablet To Navigate But Even That Doesn't Read Very Well  Am Is Pushin Me To My Limit,  

If You Have Any Idea Besides Restarting My Pc Which I Have Done Three Times.....

Another Thing I Would Like To Know Is How Do I Get My Pc To Read My Usb Cable Connecting To My Nokia 6680........i Could No Tget My Bluetooth To Work And I Don't Nthink Anyone Helped My Wen I Posted Asking For Help On This Subject So I Take It Bluetooth Doen't Work On Linux

Another Thing My Scan Won't Work Either I Have Tried To Install A Few Things And I Got Stuck Wen It Came To Installing The Driver From The Website.......


Plz People I Would Appreciate Anyhelp That Anyone Can Offer And If I Am Asking Things The Wrong Way Plz Tell Me I Have Tried So Many Time To Get People To Help Me Here But No One Does And I Really Don't Want To Go Back To Windows......... I Know Everything I Am Bitching About Works On Linux, But This Is Why Ppl Stay With Windows Cause It's So Hard To Get Help With The Simple Things That Are Needed Everyday ..........help Help Help Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Jussi Kukkonen on 2006-12-24
I can't help you straight away, but I can give some advice on asking for help:

1. Use a descriptive title, that's what hundreds of people see
2. only include one problem per post -- both your post and the following conversation get too complicated otherwise
3. Try to be exact and concise. As an example "I Put My Usb In My Port And Now My Pc Won't Pic Up My Mouse": What did you connect? Has your mouse ever worked? Is it a usb mouse? It's difficult, but we really need both the big picture and the little details before we can help.

As a general usb debugging advice: run 
```
tail -f -n0 /var/log/messages

```
in a terminal, then connect the usb device. You should get some debugging output, paste it here.

---

### Post by meng on 2006-12-24
1. Take a deep breath! (Most important)
2. Try to solve one problem at a time, provide details (as the previous poster said)
3. There's little to be gained by insulting Linux while you're asking the community for help.
4. If you can't be bothered responding in your own thread, others will assume you've given up, and won't waste time offering help.

---

