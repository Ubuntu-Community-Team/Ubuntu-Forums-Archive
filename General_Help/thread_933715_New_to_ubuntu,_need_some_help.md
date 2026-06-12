---
title: "New to ubuntu, need some help"
date: 2008-09-29
forum: General Help
---

### Post by bliztcat21 on 2008-09-29
Ok, I did a dumb thing, I bought a game without checking to see if wine runs it. turns out Wine DOES run it, ut its been a B**** to install and get working. The game is dungeons and dragons online. I downloaded the LotROLinux launcher, made the files, compiled it, etc. after 4 hours of frustration I got the launcher to load. 

So now I have the launcher, and I can select a server, etc. but, when I hit accept to play or try to patch it, it closes. 

(LotROLinux:15390): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Unknown tag 'ul' on line 6 char 6

is the error I get (the one I have to deal with right now, I have no doubt I will hit another one after (it's just my luck, computers hate me)

But, I have used google, read the help and readme files, searched the forum, etc. I configured wine so that its running windows 2000 version.

Btw, that first error is just when I open the launcher, when I RUN it, it closes and gives me 


Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ComponentModel.Win32Exception: ApplicationName='Wine', CommandLine=' dndclient.exe -a marqjdeecnp2jjpfk4jcltzce -h 12.130.63.170:9008 --glsticketdirect hnilBR/63GWsiJ4ZfHjHQpk4j4xhNmFmNwlnHeve7Eb48IhjaesgAjae0xMrftSSCEc1ugvtAROrWX15GKJ4x5N/4XAPj0pz3XJSFxsjAjvmUx5FOLSI1rynhdJrRN0Te+pjKftNcAw+pg5kuZrPea8ozNx/s5jxzr/CtVoOfFTbIbJr2lR13e5tYjLeVjbU1TiAIyOjfvNq8eRcAm3rHm592URs4pcufgJYNcHaQAsQ44uOMLPGUgGLpfvfozRnDBFumSOjReZdI6sNGH+qQA== --chatserver 206.16.13.108:2900 --language ENGLISH --supporturl [https://tss.turbine.com/TSSTrowser/trowser.aspx](https://tss.turbine.com/TSSTrowser/trowser.aspx) --gametype DDO --supportserviceurl [https://tss.turbine.com/TSSTrowser/SubmitTicket.asmx](https://tss.turbine.com/TSSTrowser/SubmitTicket.asmx) --authserverurl [https://gls.ddo.com/GLS.AuthServer/Service.asmx](https://gls.ddo.com/GLS.AuthServer/Service.asmx) --glsticketlifetime 80000 --HighResOutOfDate', CurrentDirectory='/home/blitzcat21/.wine/drive_c/Program Files/Turbine/Dungeons & Dragons Online - Stormreach', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
  at LotROLinux.StartGame.Run () [0x00000] 
  at LotROLinux.MainWindow.StartClient () [0x00000] 
  at LotROLinux.MainWindow.GetRealmDetails () [0x00000] 
  at LotROLinux.MainWindow.AuthAccount () [0x00000] 
  at LotROLinux.MainWindow.OnBtnLoginClicked (System.Object sender, System.EventArgs e) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Button.gtk_button_clicked(IntPtr )
   at Gtk.Button.gtk_button_clicked(IntPtr )
   at Gtk.Button.Click()
   at LotROLinux.MainWindow.OnTxtPasswdActivated(System.Object sender, System.EventArgs e)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at LotROLinux.GladeApp..ctor(System.String[] args)
   at LotROLinux.GladeApp.Main(System.String[] args)



At any rate, I am reaching the end of my rope. I don't know what to do. I would REALLY appreciate any help on this.

Thanks.

---

