---
title: "F-Spot Facebook Authentication Problem"
date: 2008-09-17
forum: General Help
---

### Post by matthen on 2008-09-17
Hi there,
I installed the Facebook export plugin for F-Spot using the Plugin Manager in the Edit menu. When I select photos to export to facebook, then click Login- I am taken to a facebook page in firefox. I log in there, and am told "You may now close this window and return to the application." However F-Spot doesn't do anything. It eventually closes itself down producing the following errors at the terminal:

```

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Net.WebException: The request timed out
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Mono.Facebook.Util.GetResponseBytes (System.String url) [0x00000] 
  at Mono.Facebook.Util.GetResponse[UserInfoResponse] (System.String method_name, Mono.Facebook.FacebookParam[] parameters) [0x00000] 
  at Mono.Facebook.FacebookSession.GetUserInfo (System.Int64[] uids, System.String[] fields) [0x00000] 
  at FSpot.Exporter.Facebook.FacebookExport.HandleLoginClicked (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

```

I wonder if anyone can help me fix this?
Any help would be greatly appreciated,
Matt

---

### Post by LeahF87 on 2008-12-30
I am having the exact same issue. I have tried reinstalling F-spot (both through add/remove programs and with synaptic package manager). I have also tried reinstalling the plug-in. Still no luck. 

If anyone has a different way to export photos to Facebook that would be much appreciated as well - FBs photo uploader doesn't work for me either!

---

### Post by directhex on 2008-12-30
System.Net.WebException: The request timed out

Implies the server f-spot is trying to contact isn't responding

---

### Post by matthen on 2008-12-30
(I never found a solution...)

---

### Post by duststorm on 2009-05-27
Same for me
Using Intrepid now, maybe it's fixed in Jaunty but haven't tried

---

### Post by directhex on 2009-05-27
If it's not been reported upstream, it's not a bug and doesn't exist

If it's fixed upstream, then an ubuntu/debian bug is needed with a link to the appropriate upstream bug

---

### Post by Deutscher Alex on 2009-06-24
same problem, same output, Jaunty, GNOME f-spot 0.5.0.3

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/363067](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/363067)
last post there says a fix has been released but I have yet to find anything.

---

### Post by kseise on 2009-09-11
Same thing happening to me under Karmic Alpha 5.  Anyone actually get this to work yet?

---

### Post by ukblacknight on 2009-09-15
I'm having this issue too.

*Apparently* it's been fixed in Karmic, with version 6 of F-Spot.  I'm firing up my VM now (if it feels that it's going to work today) to see if the problem persists.

---

### Post by ukblacknight on 2009-09-15
> **ukblacknight said:**
> I'm having this issue too.

*Apparently* it's been fixed in Karmic, with version 6 of F-Spot.  I'm firing up my VM now (if it feels that it's going to work today) to see if the problem persists.

Just tried it in my VM - it's even worse!  It doesn't even give you the chance to click "Login".  So much for it being fixed :S

---

### Post by bravo sierra echo on 2009-10-04
Just found this thread as I've never made the Facebook Java photo uploader work on any machine, and have been looking around for alternatives.

After visiting the Facebook authentication page, I click "OK" on the dialogue box and F-Spot crashes - just disappears without giving any error messages.  Most annoying.

Kubuntu Jaunty, f-spot 0.5.0.3

---

### Post by davygrvy on 2009-10-14
Crashing for me too, what's the fix?

---

### Post by kseise on 2009-10-14
> **davygrvy said:**
> Crashing for me too, what's the fix?

I managed to get this working by downloading the new package off of getdeb.net.  The bug has been fixed upstream, but the new packages are not in the repositories yet.

You can get the new ones here:

[http://www.getdeb.net/search.php?keywords=f-spot](http://www.getdeb.net/search.php?keywords=f-spot)

Hope it helps.

---

### Post by directhex on 2009-10-14
(Fixed in Karmic Sat, 19 Sep 2009 12:24:56 +0100)

---

