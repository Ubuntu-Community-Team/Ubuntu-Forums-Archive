---
title: "xterm return data"
date: 2008-09-26
forum: General Help
---

### Post by Pyro.699 on 2008-09-26
Hello,

In the gnome-terminal i type "xterm" which will open up an xserver terminal. Then in that terminal i can run normal code and it will display everything properly. If there a way to make xterminal return data back to the original gnome-terminal?

Thanks
~Cody Woolaver

---

### Post by spibou on 2008-09-26
xterm will write on gnome-terminal error messages for errors xterm itself encounters and when xterm exits it will return an exit value like any other application but beyond that I don't think it will return anything else. What is it you're trying to do?

---

### Post by Pyro.699 on 2008-09-26
Basically xterm is going to be ran from a php script and i want to return the data thats processed through xterm.

---

### Post by russlar on 2008-09-26
Try the screen command, or redirecting output to a text file, and using tail -f to watch that file.

---

### Post by spibou on 2008-09-26
> **Pyro.699 said:**
> Basically xterm is going to be ran from a php script and i want to return the data thats processed through xterm.
Let's say that inside xterm the following happens:
```

prompt> echo Hello world
Hello world

```
What do you want the PHP script to see? You might find useful the **script** utility which is part of the bsdutils package.

---

### Post by Pyro.699 on 2008-09-26
> **spibou said:**
> Let's say that inside xterm the following happens:
```

prompt> echo Hello world
Hello world

```
What do you want the PHP script to see? You might find useful the **script** utility which is part of the bsdutils package.
if you said "echo hello world" in the xterm, id want the php to see "hello world"

---

### Post by spibou on 2008-09-26
Then the only solution I can think of is to do the following:
1) Arrange things so that the shell uses an unusual string as prompt.
2) Use **script** to write the session into a file.
3) Filter out the lines which start with the prompt.

It's not foolproof but I don't think you have completely defined the problem. When you run a terminal emulator you can have all kinds of programmes producing all kinds of output running on top of the emulator. As far as xterm knows, the shell prompt is just one of those outputs. You may not even have a shell running on top of xterm. So you need to describe the precise criteria by which you decide which output of which programmes you want to capture.

---

### Post by Pyro.699 on 2008-09-26
Sorry for seeming... well basically confused but i cant quite understand what it is that that does... what im going to end up doing is sending a "process name" to a java program, use ps -u cody to figure out its process id, then kill it (sounds so violent xD). I want to be able to return any problems or if the script completed succusfully.

---

### Post by spibou on 2008-09-26
I think we'll have a better chance of communicating with code. So why don't you write some short programme which comes as close as you can manage to what you're trying to do and we'll take it from there.

---

### Post by Pyro.699 on 2008-09-26
You type something like
**java scripts.getPidName gedit**
> 2953

if the user fails to provide a valid name, it prints 0 (all to the system)

```

package scripts;

import java_includes.Modules;
import java.awt.AWTException;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class getPidName {

    public static void main(String[] args) throws IOException, AWTException{
        Process p = Runtime.getRuntime().exec("ps -u cody");
        InputStreamReader reader = new InputStreamReader ( p.getInputStream () );
        BufferedReader buf_reader = new BufferedReader ( reader );
        String line;

        boolean found=false;
        
        while ((line = buf_reader.readLine ()) != null)
        {
            if (line.indexOf(args[0]) > 0) {
                System.out.println(getPid(line));
                found = true;
            }
        }
        
        if (found==false){
            //not found
            System.out.print("0");
        }
        
    }
    
    public static String getPid(String line){
        String[] spl = line.split(" ");
        return spl[0];
    }
}

```

---

### Post by spibou on 2008-09-26
```

a=$( java scripts.getPidName gedit )
if [ $a = 0 ] ; then
    # The script did not complete succesfully
else
    kill -9 $a
fi

```
The above assumes that the java programme will return a single number and nothing else.

---

### Post by Pyro.699 on 2008-09-26
Is there anyway to have that more organized? and i dont undertand all the code, because that doesnt look like PHP. 

```

    //PROCESS
    if($part1=="Process"){
        if($part2=="List"){
            $fh = shell_exec("ps -u cody");
            $_POST['history'] = "\n".$fh.$_POST['history'];
        }elseif($part2=="Kill"){
            if(is_numeric($command)){
                shell_exec("kill $command");
            }else{
                $pid = killPidName($command);
            }
        }
    }

``````

function killPidName($name){
    shell_exec("xterm -display :0.0 -e java\ scripts.getPidName\ $name");
}

```Thanks again

---

