# WorldVoiceXVE

WorldVoiceXVE 是依据 VE driver 为基础开发而成的 addon。运行于 NVDA 2019.3 以上。

主要包括有多国语音自动切换、各别语音速度设定、朗读行为客制(数字读法、中文空格间隔)等功能。

## 安装

*	下载主程序addon WorldVoiceXVE、VE 语音包addon、VE 核心包。
*	安装主驱动 addon
*	核心包可透过 WorldVoiceXVE -> 档案汇入将 zip 压缩包汇入语音组件工作区。
*	核心包分为 2 种版本，分别对应第 1 驱动与第 2 驱动使用，请留意汇入对应的工作区，如将第 1 驱动核心包汇入第 2 驱动或反之将无法正常运作
*	语音包安装方式
	*	基本：使用兼容于 Vocalizer for NVDA 的语音包addon，[官方下载点](https://vocalizer-nvda.com/downloads)。
	*	进阶：可透过各种语音包内直接复制其内的地区文件夹(ex: en, mnc, mnt)等并将其压成 zip 压缩包后透过 WorldVoiceXVE 接口的档案汇入功能汇入addon内，与核心包相同需留意汇入之工作区，如无特殊需求建议使用 addon 版本安装，因 addon 版本可共享同时提供第 1 驱动与第 2 驱动使用。

## 相依性套件

除以上安装外，为驱动 VE 核心，需安装 [VC++ Redistributable Packages 2012](https://www.microsoft.com/en-US/download/details.aspx?id=30679)的 x86 版本 (VSU_4\vcredist_x86.exe) 后即可顺利驱动。

## 使用

*	NVDA+ctrl+S 选择 WorldVoiceXVE 语音合成器。
*	NVDA+ctrl+V 有基本语音速度、音调、音量等基本设定，其中数字模式、中文空白间隔为 WorldVoiceXVE 多的客制设定。
	*	数字模式：有默认(VE 默认的读法)、自动数字(以默认语音并尽可能以数字报读)、中文数字(强制使用中文数字读法)、英文数字(强制使用英文数字读法)
	*	中文空白间隔：可设定中文间有空白时，欲停顿长度，数字愈小停顿愈短， 0 为不停顿。
*	 WorldVoiceXVE -> 自动语言切换设定：可设定不同地区所使用的语音角色。
	*	先选择地区后语音列表会列出该地区可用的语音，选择后即完成该地区与语音的对应纪录。
	*	用 unicode 编码侦测文字语言勾选后，组件会根据读到的字符侦测地区。
	*	侦测语言时忽略数字和常见标点符号勾选后，数字与标点符号会认为是默认语音的地区文字。
*	 WorldVoiceXVE -> 语音速度设定：可设定不同语音角色的朗读速度。
	*	同样先选择地区后语音列表会列出该地区可用的语音，再选择好语音后，便可于速度滑杆调整数值。
	*	速度是依不同语音区分，每个语音有各自不同的速度数值，而非依地区区分。
*	 WorldVoiceXVE -> 档案汇入：可汇入档案，可用于汇入核心包与语音包。

## 更新版本日志

### v1.1

*	新增数字模式的选项，可选择有安装的语言朗读数字并可分为数值与数字两种。
*	新增忽略文件中的语言信息的选项，此主要是避免自动切换语言勾选且原始文件就有提供语言信息但不正确时(例如中文文字确标示英文语言)可能导致无法正确朗读；或是在 word 数字会被标示成英文语言导致自动改用英文语音朗读的状况。
*	优化中文空白间隔，使中文对象与中文属性间亦可停顿
*	加入其他中文语系的接口翻译
*	略过从配置文件加载变声功能，因目前 VE driver 底层的变声功能无法正常使用且换语音时容易因设定值不符加载失败导致要删整个配置文件才能解决
*	合并 VE driver 3.1.2 的更新
*	其他细部优化

### v1.2

*	提供第 2 驱动核心，整体相比第 1 驱动核心顺畅，无偶尔速度不一致与小爆音问题
*	第 2 驱动功能比照第 1 驱动包括数字模式、中文空白间隔、忽略文件中的语言信息等选项
*	第 2 驱动提供各语音速度、音调、音量各别调整，但与第 1 驱动对应数值不同，亦即第 1 驱动的速度 50 与 第 2 驱动的速度 50 不会有相同的语音速度
*	修正数字模式在选择各数值语音下时间与小数点无正确朗读的问题
*	修正无定义字符地区信息时不朗读的问题
*	修正数字模式在选择各数字语音下无正确使用选择的语音的问题
*	调整数字模式与忽略文件中的语言信息处理顺序，更符合预期朗读逻辑