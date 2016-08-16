PS4 3.55 Unsigned Code Execution
==============
This GitHub Repository contains all the necessary tools for getting PoC Unsigned Code Execution on a Sony PS4 System with firmwares 3.15, 3.50 and 3.55. <br />
This Exploit, is based-off [Henkaku's](https://henkaku.xyz/) WebKit Vulnerability for the Sony's PSVita. <br />
It includes basic ROP and is able to return to normal execution. <br />

Pre-Requisites:
==============
1. A PC
  1. Running Windows, macOS or Linux
  2. A already set up basic server where the PS4 User's Guide launcher will point for loading the payload
  3. [Python](https://www.python.org/downloads/) 2.7.X
    * Python 3.X gives problems, since they included major changes on the syntax and on the libraries in comparison with 2.7
2. A Sony PlayStation 4
  1. Running the following firmwares:
    * 3.15, 3.50 or 3.55
3. Internet Connection (PS4 and PC directly wired to the Router is the mostly preferred option)

Usage:
==============
There are two different methods to execute the Exploit, but first let's clarify how we will know which one to use. <br />
If your PlayStation 4 has got an already set-up PlayStation Network Account on it, you should use method 1. <br />
Else, if your PlayStation 4 -NEVER- had a PlayStation Network Account on it, you should use method 2. <br />
Probably you will ask why, it's pretty much easy to explain and understand: <br />
When you buy a PS4, comes unactivated, meaning that nobody has entered SEN Account on it. (Method 2) <br />
Once you use a SEN Account on it, the PS4 becomes an activated console. (Method 1) <br />
This doesn't affect the actual payload, but you should take in mind which method use. <br />

Method 1:
==============
Run this command on the folder you've downloaded this repo: <br />
`python server.py` <br />
All the debug options will be outputted during the Exploit process. <br />
Navigate to your PS4's Web Browser and simply type on the adress bar, your PC's IP Adress. <br />
Wait until the exploit finishes, once it does, PS4 will return to it's normal state. <br />
An example of what will look like found [HERE](https://gist.github.com/Fire30/2e0ea2d73d3a1f6f95d80aea77b75df8). <br />

Method 2:
==============
A dns.conf file which is present on the source, needs to be edited accordingly your local PC's IP Adress. <br />
PlayStation 4's DNS Settings must be changed in order to point the PC's IP Adress where the Exploit is located. <br />
Once you've edited the dns.conf file, simply run the next command on the folder where you downloaded this repo: <br />
`python fakedns.py -c dns.conf` <br />
And then: <br />
`python server.py` <br />
All the debug options will be outputted during the Exploit process. <br />
Once Python part is done, get into your PlayStation 4, navigate to the User's Guide page and wait until exploit finishes out. <br />
An example of what will look like found [HERE](https://gist.github.com/Fire30/2e0ea2d73d3a1f6f95d80aea77b75df8). <br />

Miscellaneous:
==============
If you want to try the socket test, change the IP Address located at the bottom of the ps4sploit.html file with your computer's one and run this command: <br />
`netcat -l 0.0.0.0 8989 -v`  <br />
You should see something like: <br />
```
Listening on [0.0.0.0] (family 0, port 8989)
Connection from [192.168.1.72] port 8989 [tcp/sunwebadmins] accepted (family 2, sport 59389)
Hello From a PS4!
```
Notes about this exploit:
==============
* Currently, the exploit does not work 100%, but is around 80% which is fine for our purposes. <br />
* Although it is confirmed to work, sometimes will fail, just wait some seconds and re-run the payload. <br />
* Performing too much memory allocation after sort() is called, can potentially lead to more instability and it may crash more. <br />
* The process will crash after the ROP payload is done executing. <br />
* This is only useful for researchers. There are many many more steps needed before this becomes useful to normal users. <br />

Acknowledgements
================
xyz - Much of the code is based off of his code used for the Henkaku project  
Anonymous contributor - WebKit Vulnerability PoC  
CTurt - I basically copied his JuSt-ROP idea  
xerpi - Used his idea for the socket code  
rck\`d - Finding bugs such as not allocating any space for a stack on function calls
Maxton - 3.50 support and various cleanup
Thunder07 - 3.15 support


Contributing
================
The code currently is a bit of a mess, so if you have any improvements feel free to send a pull request or make an issue. Also I am perfectly fine if you want to fork and create your own project.
