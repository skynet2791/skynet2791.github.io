## 一、更改设置

### 1. 显示空格

菜单栏的文件=>首选项=>设置，输入框中输入Render Whitespace，选为all

### 2. 相对行号

配合vim插件使用时可设置。设置中搜索lineNumbers，将`Editor: Line Numbers`下拉选项选择`relative`。

### 3. 保存时去掉行尾的空格

菜单栏的文件=>首选项=>设置，输入框中输入`files.trimTrailingWhitespace`，打勾选中，即可使保存文件时自动删除行尾空格。

### 4.自定义语言配色方案

vscode默认的颜色不太丰富，表达的信息有限，通过更改用户的settings.json可以指定语法元素的配色，来取得更好的显示效果，在json中添加或更改该条目：

```json
"editor.semanticTokenColorCustomizations": {
    "enabled": true,
    "rules": {
        "*.static": {
            "foreground": "#EEDEB0",
            "fontStyle": "bold italic"
        },
        "parameter": {
            // "foreground": "#C8ECFF",
            "fontStyle": "underline"
        },
        "namespace": {
            "foreground": "#EB984E"
        },
        "method": {
            "foreground": "#eac09b",
            // "fontStyle": "bold italic"
        },
        "property": {
            "foreground": "#9beac0",
            // "fontStyle": "bold italic"
        },
        "class": "#9b9dea"
    }
}
```

上述配置对静态数据、函数参数、命名空间、函数（方法）、成员变量（属性）、类（结构体）的显示颜色或格式做出了调整，以便在阅读代码时区分它们。

## 二、插件安装

### 直接安装使用：

### 1. Vim

使用Vim模式操作文件。

### 2. Git History

提供git历史版本查看和对比功能。

### 3. C/C++ Outline

**注意：此插件需要华为内网：通过VSCode-huawei安装，可在官方VSCode版本同步使用**

云核研发工具组为开发人员提供的 VSCode 插件，针对 C/C++ 提供了增强版大纲，工作区符号搜索，全局搜索，#ifdef 等折叠能力。

建议显示在右侧边栏。

### 4. WSL

提供remote到wsl进行编辑的功能，编辑虚拟机内的代码文件夹内容。

### 5. Gitlens

方便git操作

### 需要配置才有最佳体验：

### 1. Todo Tree

高亮代码中的TODO等关键字。侧边栏可以展示和跳转。

```json
//todo-tree 标签配置  标签兼容大小写字母(很好的功能!!!)
    "todo-tree.regex.regex": "((%|#|//|<!--|^\\s*\\*)\\s*($TAGS)|^\\s*- \\[ \\])",
    "todo-tree.general.tags": [
        "todo",  //添加自定义的标签成员,将在下面实现它们的样式
        "bug",
        "tag",
        "done",
        "mark",
        "test",
        "update"
    ],
    "todo-tree.regex.regexCaseSensitive": false,
    "todo-tree.highlights.defaultHighlight": {  //如果相应变量没赋值就会使用这里的默认值
        "foreground": "black",      //字体颜色
        "background": "yellow",     //背景色
        "icon": "check",            //标签样式 check 是一个对号的样式
        "rulerColour": "yellow",    //边框颜色
        "type": "tag",              //填充色类型  可在TODO TREE 细节页面找到允许的值
        "iconColour": "yellow"      //标签颜色
    },
    "todo-tree.highlights.customHighlight": {

        //todo 		需要做的功能
        "todo": {
            "icon": "issue-draft",          //标签样式
            "background": "#c9c552",  //背景色
            "rulerColour": "#c9c552", //外框颜色
            "iconColour": "#c9c552",  //标签颜色
        },

        //bug		必须要修复的BUG
        "bug": {
            "background": "#eb5c5c",
            "icon": "bug",
            "rulerColour": "#eb5c5c",
            "iconColour": "#eb5c5c",
        },

        //tag		标签
        "tag": {
            "background": "#38b2f4",
            "icon": "tag",
            "rulerColour": "#38b2f4",
            "iconColour": "#38b2f4",
            "rulerLane": "full"
        },

        //done		已完成
        "done": {
            "background": "#5eec95",
            "icon": "check",
            "rulerColour": "#5eec95",
            "iconColour": "#5eec95",
        },

        //mark     	标记一下
        "mark": {
            "background": "#f90",
            "icon": "bookmark",
            "rulerColour": "#f90",
            "iconColour": "#f90",
        },

        //test		测试代码
        "test": {
            "background": "#df7be6",
            "icon": "flame",
            "rulerColour": "#df7be6",
            "iconColour": "#df7be6",
        },

        //update  	优化升级点
        "update": {
            "background": "#d65d8e",
            "icon": "versions",
            "rulerColour": "#d65d8e",
            "iconColour": "#d65d8e",
        }
    },
```



### 2. highlight-words

选中后相同内容高亮。

* 精确匹配：比如选中代码：editUserForm，那么仅仅将选中的代码高亮，editUserFormRef就不会高亮。

  将`highlightwords.defaultMode`从0改为1。[参考链接](https://blog.csdn.net/weixin_44689966/article/details/124702989)

* 需要配置一些快捷键

  1. 选中关键字的高亮/取消高亮、取消全部等。可改为F4选中/取消高亮，F6取消全部。

  2. 上一个/下一个关键字：建议改为Ctrl+←和Ctrl+→。

* 可配置背景高亮，可改为使用9种颜色同时高亮：

  [颜色风格配置参考链接](https://blog.csdn.net/qq_29173507/article/details/111570867)

  settings.json

```json
    "highlightwords.colors": [
        {
            "dark" : "yellow"
        },
        {
            "light": "#e6ffb3",
            "dark": "pink"
        },
        {
            "light": "#b3b3ff",
            "dark": "lightgreen"
        },
        {
            "light": "#ffd9b3",
            "dark": "magenta"
        },
        {
            "light": "#ffb3ff",
            "dark": "cornflowerblue"
        },
        {
            "light": "#b3ffb3",
            "dark": "orange"
        },
        {
            "light": "#ffff80",
            "dark": "green"
        },
        {
            "light": "#b3d9ff",
            "dark": "cyan"
        },
        {
            "light": "#d1e0e0",
            "dark": "red"
        }
    ],
    "highlightwords.box": {
        "light": true,
        "dark": false
    },
```

### 3. clangd

介绍：

https://zhuanlan.zhihu.com/p/364518020

https://blog.csdn.net/tyKuGengty/article/details/120119820

需要先安装clangd server。可由在VSCode下载插件弹出提示自动安装，若不能自动安装，可以手动下载。然后将下载的文件解压，bin目录的clangd可执行文件放置在/usr/bin，lib目录里的文件放置在/usr/lib。

用户配置json

```json
    "clangd.arguments": [
        // 在后台自动分析文件（基于complie_commands)
        "--background-index",
        // 标记compelie_commands.json文件的目录位置
        // "--compile-commands-dir=build",
        // 同时开启的任务数量
        "-j=6",
        // clang-tidy功能
        // "--clang-tidy",
        // "--clang-tidy-checks=performance-*,bugprone-*",
        // 全局补全（会自动补充头文件）
        // "--all-scopes-completion",
        // 更详细的补全内容
        "--completion-style=detailed",
        // 补充头文件的形式
        "--header-insertion=never",
        // pch优化的位置
        "--pch-storage=disk",
  ],
```

配置文件.clangd

不警告未使用头文件

```yaml
Diagnostics:
    Suppress: [unused-includes]
```



### 4. clang-format

代码格式化工具，可通过工程目录里的.clang-format文件配置。

安装后需要在Windows或WSL安装clang-format可执行程序来配合。如果VSCode是remote到20.04的Ubuntu工作，需要增加Ubuntu的软件源来安装：

* Focal (Ubuntu 20.04)

      deb http://apt.llvm.org/focal/ llvm-toolchain-focal main
      deb-src http://apt.llvm.org/focal/ llvm-toolchain-focal main
      # 14
      deb http://apt.llvm.org/focal/ llvm-toolchain-focal-14 main
      deb-src http://apt.llvm.org/focal/ llvm-toolchain-focal-14 main
      # 15
      deb http://apt.llvm.org/focal/ llvm-toolchain-focal-15 main
      deb-src http://apt.llvm.org/focal/ llvm-toolchain-focal-15 main
  
  #### 配置参考
  
  ```shell
  ---
  # 语言:
  # - None: 
  # - Cpp: 
  # - Java: 
  # - JavaScript: 
  # - ObjC: 
  # - Proto: 
  # - TableGen: 
  # - TextProto: 
  Language: Cpp
  
  # 基于的编码规范, 可选:
  # - LLVM: https://llvm.org/docs/CodingStandards.html
  # - Google: https://google.github.io/styleguide/cppguide.html
  # - Chromium: https://chromium.googlesource.com/chromium/src/+/refs/heads/main/styleguide/styleguide.md
  # - Mozilla: https://firefox-source-docs.mozilla.org/code-quality/coding-style/index.html
  # - WebKit: https://www.webkit.org/coding/coding-style.html
  # - Microsoft: https://docs.microsoft.com/en-us/visualstudio/ide/editorconfig-code-style-settings-reference
  # - GNU: https://www.gnu.org/prep/standards/standards.html
  # - InheritParentConfig: 继承父目录的编码规范, 如果有的话, 不是一个真正的编码规范
  # - None: 不使用, 即自动配置, 也就是本文件中的自定义内容
  BasedOnStyle: Google
  
  # 访问声明符缩进
  AccessModifierOffset: -4
  
  # 开括号后的参数(函数的参数)对齐(包括小括号/大括号/尖括号), 建议使用 Align
  # - Align: 对于开括号, 即在换行情况下, 换行的参数跟开括号对齐, 建议使用
  # - DontAlign: 不对于开括号, 即换行时使用配置的空格数
  # - AlwaysBreak: 永远换行, 即第一个参数都不允许粘连括号, 会强制换行, 换行后使用配置空格数对齐
  # - BlockIndent: 同 AlwaysBreak, 多了一个操作: 如果参数不固定在同一行, 闭括号将在下一行
  AlignAfterOpenBracket: Align
  
  # 结构休数组统一初始化对齐, 建议不配置, 没过多必要, 详见 clang-format doc
  # - None: 不做处理, 即保留开发者的代码
  # - Left: 左对齐
  # - Right: 右对齐
  AlignArrayOfStructures: None
  
  # 连续赋值语句的对齐，即多个赋值语句连续出现时的对齐策略配置, 包含多个子配置项
  AlignConsecutiveAssignments:
    # 是否启用, 建议 false
    Enabled: false
    # 是否跨过空行, 即多个对齐语句中间有空行时, 是否跨过, 如果要开启连续赋值语句的配置, 建议 false
    AcrossEmptyLines: false
    # 是否跨过注释, 建议 false
    AcrossComments: false
    # 是否跨过复合语句(包括空行及注释), 建议 false
    AlignCompound: false
    # 是否(右)对齐赋值操作的操作符, 建议 true
    PadOperators: true
  
  # 同 AlignConsecutiveAssignments , 表示连续位定义语句出现时, 是否需要对齐:符号, 位变量定义用得少, 可以不开启
  AlignConsecutiveBitFields:
    # 是否启用, 建议 false
    Enabled: false
    # 是否跨过空行, 即多个对齐语句中间有空行时, 是否跨过, 如果要开启连续赋值语句的配置, 建议 false
    AcrossEmptyLines: false
    # 是否跨过注释, 建议 false
    AcrossComments: false
    # 是否跨过复合语句(包括空行及注释), 建议 false
    AlignCompound: false
    # 是否(右)对齐赋值操作的操作符, 建议 true
    PadOperators: false
  
  # 是否对齐连续声明
  AlignConsecutiveDeclarations:
    Enabled: false
    AcrossEmptyLines: false
    AcrossComments: false
    AlignCompound: false
    PadOperators: false
  AlignConsecutiveMacros:
    Enabled: false
    AcrossEmptyLines: false
    AcrossComments: false
    # 只在 AlignConsecutiveAssignments 配置中有效, 自动生成的 clang-format 有此项, 忽略
    AlignCompound: false
    # 只在 AlignConsecutiveAssignments 配置中有效, 自动生成的 clang-format 有此项, 忽略
    PadOperators: false
  
  # 续行符(\\)对齐:
  # - DontAlign: 不做操作
  # - Left: 尽可能向左对齐, 即最长一行代码为准
  # - Right: 跟开发都写的最远的\\对齐(即不会自动缩减你的空格), 建议使用这个
  AlignEscapedNewlines: Right
  
  # 在二元/一元表达式中的操作数对齐, 可选值:
  # - DontAlign: 不做对齐, 在操作数换行后, 将使用 ContinuationIndentWidth 来对齐
  # - Align: 即换行时, 操作数( or 操作符加操作数)跟上一行的第一个操作数左对齐, 具体操作符要不要换行,
  #          由 BreakBeforeBinaryOperators 配置决定
  AlignOperands: Align
  
  AlignTrailingComments: true
  AllowAllArgumentsOnNextLine: true
  AllowAllParametersOfDeclarationOnNextLine: true
  AllowShortEnumsOnASingleLine: true
  AllowShortBlocksOnASingleLine: Never
  AllowShortCaseLabelsOnASingleLine: false
  
  # 允许短的函数放在同一行
  # - None: 
  # - InlineOnly: 定义在类中
  # - Empty: 空函数
  # - Inline: 定义在类中，空函数
  # - All: 
  AllowShortFunctionsOnASingleLine: All
  
  # 允许 lambda 在一行中, 同上, 建议 All
  AllowShortLambdasOnASingleLine: All
  
  # 是否将简单的 if(else/else if) 语句中的 body 跟 if(else/else if) 放置于同一行，可选值
  # - Never: 永远不, 建议值
  # - WithoutElse: 没有 else/else if 时, 允许
  # - OnlyFirstIf: 只有第一个 if 允许
  # - AllIfAndElse: 所有的 if/else 都允许
  AllowShortIfStatementsOnASingleLine: Never
  
  # 是否允许 loop 语句体跟 loop 语句共行, true/false , 建议 false
  AllowShortLoopsOnASingleLine: false
  
  # Deprecated, 废弃定义, 设置为 None 即可
  AlwaysBreakAfterDefinitionReturnType: None
  
  # Return 类型后是否换行, 诡异的定义, 请设置为 None 即可
  AlwaysBreakAfterReturnType: None
  
  # 多常量字符串定义是, 是否在第一个字符串常量前换行, true/false , 建议 false
  AlwaysBreakBeforeMultilineStrings: false
  
  # 模板声明换行风格, 可选值:
  # - No: 永远不对开发者的风格作处理
  # - MultiLine: 建议值, 即仅在开发者写的模板声明(包括函数)跨越多行时, 进行换行, 否则维持原样
  # - Yes: 不管如何都进行分行, 不建议
  AlwaysBreakTemplateDeclarations: MultiLine
  # 属性宏列表, 自定义, 用于语言扩展或静态分析注解, 可忽略
  AttributeMacros:
    - __capability
  # 函数调用时的参数(Arguments)是否放置于一行, false不放置, true强制一个调用参数一行, 建议false
  BinPackArguments: false
  # 函数定义参数(Parameters)是否放置于一行, 同BinPackArguments
  BinPackParameters: false
  
  # 大括号换行
  BraceWrapping:
    # 在case后的大括号是否换行
    AfterCaseLabel: true
    # class后
    AfterClass: true
    # 控制语句(if/for/while/switch/...)后是否换行
    # - Never: 永远不, 即永远将语句体的大括号放置于控制语句同一行
    # - MultiLine: 多行控制语句才进行换行
    # - Always: 永远换行, 建议
    AfterControlStatement: Always
    # 下面比较容易理解, 不再作无意义的解释
    AfterEnum: true
    AfterFunction: true
    AfterNamespace: true
    AfterObjCDeclaration: true
    AfterStruct: true
    AfterUnion: true
    AfterExternBlock: true
    BeforeCatch: false
    BeforeElse: true
    BeforeLambdaBody: false
    BeforeWhile: false
    IndentBraces: false
    SplitEmptyFunction: true
    SplitEmptyRecord: true
    SplitEmptyNamespace: true
  # 二元操作符前是否换行, 建议为 None
  BreakBeforeBinaryOperators: None
  # 概念声明前是否换行, 建议 Always
  BreakBeforeConceptDeclarations: Always
  # 大括号换行风格,Custom即可, 具体值可参考上方文档
  BreakBeforeBraces: Custom
  # 继承列表括号前换行, false即可
  BreakBeforeInheritanceComma: false
  # 是否将整个继承列表换行
  BreakInheritanceList: BeforeColon
  BreakBeforeTernaryOperators: true
  # 是否在构造函数初始化列表的,前换行
  BreakConstructorInitializersBeforeComma: false
  # 继承列表换行风格, 使用BeforeComma适合
  BreakConstructorInitializers: BeforeComma
  # Java注解相关, 跳过
  BreakAfterJavaFieldAnnotations: false
  # 字面字符串是否换行, true
  BreakStringLiterals: true
  # 代码列字符上限
  ColumnLimit: 120
  # pragma注释
  CommentPragmas: '^ IWYU pragma:'
  # 注释关键字对齐(const/volatile), 建议Leave
  # - Leave: - 不改变开发者定义
  # - Left: 位于类型前
  # - Right: 位于类型后
  # - Custom: 自定义
  QualifierAlignment: Leave
  # 未在文档中找到
  CompactNamespaces: false
  # 构造函数初始化列表缩进, 建议0
  ConstructorInitializerIndentWidth: 0
  # 函数调用续行对齐, 建议4
  ContinuationIndentWidth: 4
  # C++11的统一初始化列表大括号风格, 建议true
  Cpp11BracedListStyle: true
  # 提取行结束符并标准化, 建议false, 不要进行分析及自动运用, 而是强制使用UseCRLF设定来做
  DeriveLineEnding: true
  # 是否开启文件分析, 根据文件中的*/&使用情况更新clang-format设定, 在无法决定时, 使用PointerAlignment代替, 不建议开启
  DerivePointerAlignment: false
  DisableFormat: false
  # 访问限定后是否添加空行, 建议Never
  EmptyLineAfterAccessModifier: Never
  # 访问限定前是否要求空行, 建议LogicalBlock
  EmptyLineBeforeAccessModifier: LogicalBlock
  # 实验性的自动检测同行并进行操作，建议 false
  ExperimentalAutoDetectBinPacking: false
  # 是否打包构造函数初始化列表, 建议Never, 可选:
  # - Never: 永远不做操作, 即一个参数一行
  # - BinPack: 两个参数一行
  # - CurrentLine: 所有参数放置于一行, 如果放不下, 就一个参数一行
  # - NextLine: 同CurrentLine有点像, 唯一不同就是如果放不行, 将剩余参数放置于下一行(即不自动一参一行)
  PackConstructorInitializers: Never
  BasedOnStyle: ''
  # 废弃配置
  ConstructorInitializerAllOnOneLineOrOnePerLine: false
  # 废弃配置
  AllowAllConstructorInitializersOnNextLine: true
  # 是否强制在namespace结尾增加 // namespace xxx, 建议为true
  FixNamespaceComments: true
  # 大于多少行namespace内的代码行时才在namespace结尾添加 // namespace xxx, 建议0，即无论如何都添加
  ShortNamespaceLines: 0
  # Macro宏
  ForEachMacros:
    - foreach
    - Q_FOREACH
    - BOOST_FOREACH
  #If宏
  IfMacros:
    - KJ_IF_MAYBE
  # include代码块操作, 前提是SortIncludes开启:
  # - Preserve: 只对每个代码块排序
  # - Merge: 对所有代码块合并, 并在合并后排序
  # - Regroup: 对所有include块进行分析, 并重新分块, 不建议!
  IncludeBlocks: Preserve
  # Include Sort选项, 可选:
  # - Never: 永远不, 建议
  # - CaseSensitive: 大小写敏感排序
  # - CaseInsensitive: 大小写不敏感排序
  SortIncludes: Never
  # Include种类, 默认即可
  IncludeCategories:
    - Regex: '^"(llvm|llvm-c|clang|clang-c)/'
      Priority: 2
      SortPriority: 0
      CaseSensitive: false
    - Regex: '^(<|"(gtest|gmock|isl|json)/)'
      Priority: 3
      SortPriority: 0
      CaseSensitive: false
    - Regex: '.*'
      Priority: 1
      SortPriority: 0
      CaseSensitive: false
  IncludeIsMainRegex: '(Test)?$'
  IncludeIsMainSourceRegex: ''
  # 缩进访问控制
  IndentAccessModifiers: false
  # 缩进case语句, 建议 false
  IndentCaseLabels: false
  # 缩进case body, 建议true
  IndentCaseBlocks: true
  # 缩进goto标签
  IndentGotoLabels: true
  # 预处理指示(PPD-PreProcessor Directive)缩进, 建议None
  # - None: 不缩进
  # - AfterHash: #不缩进, #后面的指示缩进
  # - BeforeHash: #跟前缩进
  IndentPPDirectives: None
  # extern "C"缩进, 建议AfterExternBlock
  IndentExternBlock: AfterExternBlock
  # 模板require是否缩进
  IndentRequiresClause: true
  # 缩进宽度
  IndentWidth: 4
  # 函数名换行时, 是否缩进(即返回值跟名字不同行时), 建议false
  IndentWrappedFunctionNames: false
  # 是否在代码块中(if/else/for/do/while)强制插入大括号, 建议false
  InsertBraces: false
  # 是否强制插入拖尾的',', 建议为None
  InsertTrailingCommas: None
  # Java相关, 跳过
  JavaScriptQuotes: Leave
  JavaScriptWrapImports: true
  # 是否block开始前有一个empty line, 诡异, 直接false
  KeepEmptyLinesAtTheStartOfBlocks: false
  # 未找到定义
  LambdaBodyIndentation: Signature
  # 宏开始的正则, 不使用
  MacroBlockBegin: ''
  # 宏结束的正则, 不使用
  MacroBlockEnd: ''
  # 空行保持, 建议为1
  MaxEmptyLinesToKeep: 1
  # Namespace内的对齐, 直接使用None即可, 即所有namespace内(包括内嵌的)都不indent
  NamespaceIndentation: None
  # Obj-C语言设置, 跳过
  ObjCBinPackProtocolList: Auto
  ObjCBlockIndentWidth: 4
  ObjCBreakBeforeNestedBlockParam: true
  ObjCSpaceAfterProperty: false
  ObjCSpaceBeforeProtocolList: true
  # 罚分设定(根据你的"违规"值选择罚分少的)
  PenaltyBreakAssignment: 2
  PenaltyBreakBeforeFirstCallParameter: 19
  PenaltyBreakComment: 300
  PenaltyBreakFirstLessLess: 120
  PenaltyBreakOpenParenthesis: 0
  PenaltyBreakString: 1000
  PenaltyBreakTemplateDeclaration: 10
  PenaltyExcessCharacter: 1000000
  PenaltyReturnTypeOnItsOwnLine: 60
  PenaltyIndentedWhitespace: 0
  # 指针对齐, 建议Right
  PointerAlignment: Right
  # 引用对齐, 可选:
  # - Pointer: 使用'PointerAlignment'配置, 建议使用
  # - Left: Left
  # - Right: Right
  ReferenceAlignment: Pointer
  # 预处理对齐宽度
  PPIndentWidth: -1
  # 是否允许clang-format尝试重新粘合注释(true/false), 不建议使用
  ReflowComments: false
  # 是否移除多余的{}, 不建议
  RemoveBracesLLVM: false
  # 模板中的require语句位置, 建议OwnLine
  RequiresClausePosition: OwnLine
  # 分隔不同定义块, 建议Always, 可选:
  # - Leave - 不处理, 建议, 即由业务决定, 也可以使用Always
  # - Always - 永远进行分隔
  # - Never: 永远 不进行, 不建议
  SeparateDefinitionBlocks: Leave
  # Java项, 跳过
  SortJavaStaticImport: Before
  # 排序using语句(true/false), 不建议开启
  SortUsingDeclarations: false
  # C风格cast的类型括号后面是否增加space(true/false), 比较诡异, 建议false
  SpaceAfterCStyleCast: false
  # 逻辑非操作(!)后面是否加space(true/false), 比较诡异, 建议false
  SpaceAfterLogicalNot: false
  # template关键字后面是否加space(true/false), 建议true, 即template <xxx>, 而不是template<xxx>
  SpaceAfterTemplateKeyword: true
  # 赋值语句操作符前是否添加space(true/false), 建议true
  SpaceBeforeAssignmentOperators: true
  # case语句:前是否增加space(true/false), 建议false
  SpaceBeforeCaseColon: false
  # c++11的统一初始化列表的大括号中是否添加space(true/false), 建议false
  SpaceBeforeCpp11BracedList: false
  # 构造函数初始化列表:前是否加space(true/false), 建议false
  SpaceBeforeCtorInitializerColon: false
  # 继承列表的:前是否加space(true/false), 建议true
  SpaceBeforeInheritanceColon: true
  # 圆括号前是否增加空格: 建议只在控制语句的贺括号前增加, 即配置为ControlStatements即可
  SpaceBeforeParens: ControlStatements
  # SpaceBeforeParens为Custom时使用
  SpaceBeforeParensOptions:
    AfterControlStatements: true
    AfterForeachMacros: true
    AfterFunctionDefinitionName: false
    AfterFunctionDeclarationName: false
    AfterIfMacros: true
    AfterOverloadedOperator: false
    AfterRequiresInClause: false
    AfterRequiresInExpression: false
    BeforeNonEmptyParentheses: false
  # 指针修饰的space添加, 建议Default, 即使用PointerAlignment代替
  SpaceAroundPointerQualifiers: Default
  # Loop关键字前前是否增加space, 建议true
  SpaceBeforeRangeBasedForLoopColon: true
  # 空body是否添加space, 建议true
  SpaceInEmptyBlock: true
  # 圆括号前是否增加space, 建议false, true太多影响代码紧凑
  SpaceInEmptyParentheses: false
  # Trailing注释前的空格数, 建议1
  SpacesBeforeTrailingComments: 1
  # <>里面是否增加space, 不建议, 配置成Never即可
  SpacesInAngles: Never
  # 条件语句()里面是否增加space, 不建议, 配置成Never即可
  SpacesInConditionalStatement: false
  # 容器初始化列表[]/{}里面是否增加space, 不建议(跟C++11风格保持一致)
  SpacesInContainerLiterals: false
  # C风格的转换()里面是否增加space, 不建议
  SpacesInCStyleCastParentheses: false
  # 行注释前的空格范围数量, 建议Maximum关闭, 设置成-1, 即//到你的注释内容前的空格数量至少是1, 至多是无穷
  SpacesInLineCommentPrefix:
    Minimum: 1
    Maximum: -1
  # 贺括号内是否加space, false
  SpacesInParentheses: false
  # 中括号内是否加space, false
  SpacesInSquareBrackets: false
  # 大括号内是否加space, false
  SpaceBeforeSquareBrackets: false
  # 位定义:前后是否增加空格, 可选:
  # - Both: 前后都添加
  # - Before: 只在前增加
  # - After: 只在后增加
  # - None: 不增加, 建议, 没有必要因为过多的space(s)影响代码紧凑
  BitFieldColonSpacing: None
  # C++标准, Latest即可
  Standard: Latest
  StatementAttributeLikeMacros:
    - Q_EMIT
  StatementMacros:
    - Q_UNUSED
    - QT_REQUIRE_VERSION
  # Tab宽度, 建议4
  TabWidth: 4
  # 不使用CRLF, 强制关闭, 如果DeriveLineEnding为true却未自动决策出来, 此项用于fallback策略
  UseCRLF: false
  # Tab使用, 没有必要使用, 直接Never
  UseTab: Never
  # 空格敏感宏列表
  WhitespaceSensitiveMacros:
    - STRINGIZE
    - PP_STRINGIZE
    - BOOST_PP_STRINGIZE
    - NS_SWIFT_NAME
    - CF_SWIFT_NAME
  ```
  
  

## 三、其他

### 编译数据库

#### 何为编译数据库

编译数据库是用于存储编译选项的数据库。它记录了用于在项目中编译文件的编译选项。编译数据库可以是但不限于JSON编译数据库（一个名为compile_commands.json的JSON格式文件）。json格式较为常见。

#### 如何生成编译数据库

* make或其他构件系统：

  1. 使用strace命令：`strace -v -s 65535 -e trace=execve -f -o strace.log bash build.sh`

  2. 使用python脚本cc_strace.py转换strace.log为compile_commands.json编译数据库

     `python cc_strace.py strace.log > compile_commands.json`

  3.  在这里生成的编译数据库需要继续处理，先将compile_commands.json另存为compile_commands.json.orig，再通过python脚本生成最终的编译数据库

     `python3 cc_transform.py --transform-compdb --compdb-src compile_commands.json.orig --compdb-out compile_commands.json`

     补充需要的库：

     ```shell
     pip install -U regex
     ```

  4. 注意这里使用的是Python3

### GDB调试

[vscode c++远程调试实战 - 后端技术小屋](https://backendhouse.github.io/post/vscode-c++%E8%BF%9C%E7%A8%8B%E8%B0%83%E8%AF%95%E5%AE%9E%E6%88%98/)
