# conky-tab
`conky-tab` contains a configuration file for **Conky** (a free, light-weight system monitor for X, that displays any kind of information on your desktop), that allow to monitoring system's resources (like CPU, memory, disk usage, etc) and a way to embed a linux terminal with **Tilda** (a terminal emulator that does not behave like a normal window but instead it can be pulled up and down from the top of the screen) on the desktop side.  

## Monitoring Sidebar
First install conky and conky-manager:
```bash
$ sudo add-apt-repository ppa:linuxmint-tr/aracla
$ sudo apt update
$ sudo apt install conky conky-all conky-manager conky-manager-extra
```
Install the conky-tab theme in the `~/.conky/Extra` folder
```bash
$ cd ~/.conky/Extra
$ git clone https://github.com/vinz-uts/conky-tab.git
```
In the `~/.conky` folder edit the `conky-startup.sh` file to run the sidebar theme 10 seconds after the user login:
```bash
sleep 10s
killall conky
cd ~/.conky/Extra/conky-tab
conky -c ~/.conky/Extra/conky-tab/conkyrc &
```
In Ubuntu 20.04 (Focal Fossa), run from the application menu the _Startup Applications Preferences' and use the button to add a new application. Set as name `Conky` and command `sh "/home/<user>/.conky/conky-startup.sh"`. The sidebar with system's resoureces information now start 10 seconds after the user login.

## Embedded Terminal
First install Tilda:
```bash
$ sudo apt install tilda
```
Move the tilda configuration file in the `~/.config/tilda` folder, which set the style and the position of the embedded terminal on the desktop side
```bash
$ mv ~/.conky/Extra/conky-tab/tilda/config_0 ~/.config/tilda/
```
Create the `tilda_startup.sh` file to run the embedded terminal 10 seconds after the user login:
```bash
sleep 10s
tilda &
```
Run the _Startup Applications Preferences' and add a new application with name `EmbeddedTerminal` and command `sh "/home/<user>/.config/tilda/tilda_startup.sh"`.