## 5\. 控件的命令列表: {#5}

### 1) PathGet {#1-pathget}

**描述：**

获取控件沙盒目录下的一个子目录的全路径，如果该子目录不存在，则创建该子目录。

**参数：**

Type：子目录的名称

**返回值：**

[字符串] 所获取的路径。

### 2) FileList {#2-filelist}

**描述：**

获取指定文件目录下的文件列表

**参数：**

Dir：指定需要获取文件列表的目录（受沙盒控制）

**返回值：**

[字符串] OML格式，包含以下参数。例如：(File1.txt){(Size){1000}(Time){2011-10-21,15:03:55}}

File：文件名

Size：文件的大小（字节）

Time：修改时间，格式：YYYY-MM-DD,HH:MM:SS

### 3) FileCopy {#3-filecopy}

**描述：**

复制一个文件。控件的文件操作只限制在沙盒目录范围内。该沙盒目录缺省为当前用户的Documents目录下的Peergine子目录。所以，需要对沙盒目录之外的文件进行操作时，使用此命令来复制文件。

**参数：**

Src：源文件路径（受沙盒控制）。当此参数为空时，系统弹出文件对话框让用户选择源文件路径。

Dst：目标文件路径（受沙盒控制）。当此参数为空时，系统弹出文件对话框让用户选择目标文件路径。

Filter：指定文件对话框中的文件扩展名过滤条件，样例：&quot;Png Files(*.png)|*.png||All files(*.*)|*.*&quot;。

**返回值：**

[整型] 1：成功，0：失败

### 4) FileMove {#4-filemove}

**描述：**

移动或重命名一个文件.

**参数：**

Src：源文件路径（受沙盒控制）。

Dst：目标文件路径（受沙盒控制）。

**返回值：**

[整型] 1：成功，0：失败

### 5) FileInfo {#5-fileinfo}

**描述：**

获取指定文件的信息，包括文件的大小、修改时间和摘要。

**参数：**

Path：指定的文件路径。

**返回值：**

[字符串] OML格式，包含以下参数。例如：(Size){1000}(Time){2011-10-21,15:04:23}(Hash){}

Size：文件的大小（字节）

Time：文件的修改时间，格式：YYYY-MM-DD,HH:MM:SS

Hash：文件的摘要，用SHA256算法生成，Base64格式。

### 6) FileClean {#6-fileclean}

**描述：**

清除指定沙盒子目录下的所有文件。

**参数：**

Type：子目录的名称

**返回值：**

无

### 7) DlgFile {#7-dlgfile}

**描述：**

弹出文件对话框，让用户选择需要打开或保存的文件。

**参数：**

Open：1为打开文件，0为保存文件

Ext：在对话框里显示的缺省扩展名

File：在对话框里显示的缺省文件名

Filter：文件扩展名过滤条件，样例：&quot;Png Files(*.png)|*.png||All files(*.*)|*.*&quot;。

**返回值：**

[字符串] OML格式，包含以下参数。例如：(Path){c:\temp\xxxx.txt}(File){xxxx.txt}

Path：文件的全路径

File：文件名

### 8) DlgDir {#8-dlgdir}

**描述：**

弹出文件目录对话框，让用户选择目录。

**参数：**

Dir：在对话框中初始化的目录。

**返回值：**

[字符串] OML格式，包含以下参数。例如：(Dir){c:\temp\image}

Dir：用户选择的目录。

### 9) CacheAdd {#9-cacheadd}

**描述：**

往文件缓冲内添加一个文件，同时把该文件复制到文件缓冲目录下。

**参数：**

Name： 文件缓冲区的名称。

URL：指定该文件在缓冲中的唯一标识。

Copy：指定需要复制的文件路径（受沙盒控制）。如果不需要复制文件，则此参数为空。

Time：设置文件的修改时间。

**返回值：**

[字符串] OML格式，包含以下参数。

例如：(Local){c:\My Document\Peergine\Cache\xxxx[0].txt}(Exist){1}

Local：文件在缓冲目录下的路径。

Exist：该记录是否已经在缓冲区存在。

### 10) CacheDelete {#10-cachedelete}

**描述：**

从文件缓冲区中删除指定的文件

**参数：**

Name： 文件缓冲区的名称。

URL：文件在缓冲区中的唯一标识。

**返回值：**

无

### 11) CacheSetDir {#11-cachesetdir}

**描述：**

指定控件的文件缓冲目录。

**参数：**

Name： 文件缓冲区的名称。

Dir：文件缓冲目录的路径（受沙盒控制）。如果路径为非空字符串，则启用该文件缓冲区。如果路径为空字符串，则关闭该文件缓冲区。

**返回值：**

[整型] 1：成功，0：失败

### 12) CacheGetInfo {#12-cachegetinfo}

**描述：**

获取文件缓冲区中指定文件的信息。

**参数：**

Name： 文件缓冲区的名称。

URL：文件在缓冲区中的唯一标识。

**返回值：**

[字符串] OML格式，包含以下参数。例如：(URL){File:xxxx.txt}(Path){c:\My Document\Peergine\ Cache\xxxx[0].txt}(Size){1000}(Time){2011-10-21,16:21:02}(Hash){}

URL：文件在缓冲区中的唯一标识。

Path：文件在缓冲目录中的全路径。

Size：文件的大小（字节）

Time：文件修改的时间，格式：YYYY-MM-DD,HH:MM:SS

Hash：文件的摘要，SHA256算法生成，Base64格式。

### 13) CookieSet {#13-cookieset}

**描述：**

在本地存储一个cookie。

**参数：**

Name：Cookie的名字

Value：Cookie的值

Expire：Cookie的过期时间，格式：YYYY-MM-DD,HH:MM:SS

**返回值：**

[整型] 1：成功，0：失败

### 14) CookieGet {#14-cookieget}

**描述：**

读取一个本地Cookie的值。

**参数：**

Name：Cookie的名字

**返回值：**

[字符串] OML格式，包含以下参数。例如：(Value){xxxxxx}

Value：Cookie的值

### 15) CookieDelete {#15-cookiedelete}

**描述：**

删除一个本地Cookie。

**参数：**

Name：Cookie的名字。

**返回值：**

无

### 16) ImageConvert {#16-imageconvert}

**描述：**

转换图片格式和缩放图片尺寸。通过文件名的后缀来指定图片的格式，如果输入、输出的文件名后缀不相同，则转换文件格式。支持的图片格式为*.bmp、*.png和*jpg三种。通过Width和Height参数的指定尺寸缩放的大小和方式，如下表：

| 宽Width | 高Height | 缩放方式 |
| --- | --- | --- |
| 不等于0 | 不等于0 | 缩放后，宽和高不超过Width和Height，宽和高的比率保持不变 |
| 不等于0 | 等于0 | 缩放后，宽为Width，宽和高的比率保持不变 |
| 等于0 | 不等于0 | 缩放后，高为Height，宽和高的比率保持不变 |
| 等于0 | 等于0 | 不缩放尺寸 |

**参数：**

In：输入的图片文件路径（受沙盒控制）

Out：输出的图片文件路径（受沙盒控制）

Width：输出的图片宽度（像素）

Height：输出的图片高度（像素）

**返回值：**

[整型] 1：成功，0：失败

### 17) HttpAdd {#17-httpadd}

**描述：**

在本地HTTP服务器中添加一个文件。

**参数：**

URL：该文件从HTTP访问的URI

Local：该文件的本地存储路径。

**返回值：**

[整型] 1：成功，0：失败

### 18) HttpDelete {#18-httpdelete}

**描述：**

从本地HTTP服务器中删除一个文件。

**参数：**

URL：该文件从HTTP访问的URI

**返回值：**

[整型] 1：成功，0：失败

### 19) HttpConfig {#19-httpconfig}

**描述：**

设置本地HTTP服务器的侦听地址且启动HTTP服务器。

**参数：**

Addr：HTTP服务器的侦听地址，格式为：X:X:X:X:Port:Info。此地址只能是IPV4 的私网IP地址或本地环回地址。例如：0:0:0:7f000001:80:0或0:0:0:127.0.0.1:80:0。如果指定的侦听地址为0:0:0:0:0:0，则关闭HTTP服务器。

**返回值：**

[整型] 1：成功，0：失败

### 20) AviPlay {#20-aviplay}

**描述：**

播放一个AVI文件。控件目前支持的AVI视频/音频格式为：

_音频：PCM或G.711A编码、16bit采样、采样速率11 KHz、单通道。_

_视频：MJPEG(A)和VP8视频压缩格式。_

如果你的AVI文件格式不符合，请先用工具转换成以上的格式后再播放。

**参数：**

File：AVI文件的路径

Wnd：显示AVI视频图像的窗尺寸口和句柄。格式样例：(PosX){0}(PosY){0}(SizeX){60}(SizeY){80} (Handle){9847387}。此参数可以用utilGetWndRect()函数从控件获取。

**返回值：**

[整型] 1：成功，0：失败

### 21) AviStop {#21-avistop}

**描述：**

停止播放一个AVI文件。

**参数：**

File：AVI文件的路径

**返回值：**

[整型] 1：成功，0：失败

### 22) AviGetInfo {#22-avigetinfo}

**描述：**

获取一个AVI文件的信息（未实现）。

**参数：**

无

**返回值：**

无

### 23) TrayIcon {#23-trayicon}

**描述：**

安装托盘图标（未实现）。

**参数：**

Icon：图标文件路径，文件名的后缀必须为.ico。此参数为空时，卸装托盘图标。

Menu：鼠标右键点击托盘图标时弹出的菜单。此参数为菜单项的信息，格式为：(菜单ID){菜单文本}。样例：(0){显示窗口}(1){设置}(){}(2){退出}。OML名称为空的菜单项为分隔线。

**返回值：**

[整型] 1：成功，0：失败

**事件：**

鼠标左键点击托盘图标：通过OnExtRequest()函数上报点击事件。格式为：(TrayIcon){}

选择托盘图标的右键菜单：通过OnExtRequest()函数上报选择的菜单ID。格式为：(TrayIcon){菜单ID}

### 24) TracePopup {#24-tracepopup}

**描述：**

在屏幕的右下角弹出一个提示框（未实现）。

**参数：**

Title：提示框标题

Text：提示框中显示的内容。

**返回值：**

[整型] 1：成功，0：失败

**事件：**

鼠标键击提示框内容：通过OnExtRequest()函数上报点击事件。格式为：(TracePopup){自定义事件内容}。

### 25) CapScreen {#25-capscreen}

**描述：**

从屏幕截取一个图片。

**参数：**

Full：是否要全屏截图。0为只截取鼠标选中的区域，1为全屏截取（未支持）

Path：存储所截取图片的文件路径，文件名的后缀必须为.png。

**返回值：**

[整型] 1：成功，0：失败

**事件：**

截图完成后：通过OnExtRequest()函数上报图片的文件路径。格式为：(Path){文件路径}。

### 26) Setting {#26-setting}

**描述：**

弹出控件的设置对话框。还可以在控件窗口内点击右键菜单打开设置对话框。

**参数：**

无

**返回值：**

[整型] 1：成功，0：失败

### 27) Version {#27-version}

**描述：**

获取控件的版本信息。

**参数：**

无

**返回值：**

[字符串] OML格式，包含以下参数。例如：(Version){v1.1.2}(OS){Windows}

Version：版本号。

OS：操作系统类型。