---
name: mulgil-kim-painter
description: 把照片或图片改画为 Mulgil Kim（金水路、김물길、Kim Mulgil）风格的水粉画。用户想把图片画成这位画家的风格时使用。
---

# Mulgil Kim 风格改画

用原图改画，交付生成的图片。画面以安静的自然氛围和哑光水粉质感为主。开画前问清梦幻程度和笔触偏好；这两项分开选，梦幻的画也可以很细腻。

## 绘画前选择参数

先看用户已经说了什么，只问还没确定的部分，一次问完：

> 这次想要一点梦幻感，还是大胆一些？笔触想松一点、适中，还是细腻？
> 配色、光线或构图有想法也可以一起说，其他就照原图来。

有用户输入工具时用它提问，也接受自由描述。等梦幻程度和笔触偏好都有回复后再生成；预选项和没回复都不算选择。等待时可以先看原图。说过的偏好不再问，也不用让用户填完七项。

| 参数 | 可选值 | 对画面的作用 | 未指定时 |
| --- | --- | --- | --- |
| 梦幻程度 | 轻微 / 明显 / 强烈 | 从自然氛围与轻微流动，到清晰的形态变化，再到更大胆的梦境空间 | 先询问，不擅自选择 |
| 笔触精细度 | 松散 / 适中 / 细腻 | 从概括色块、简化细节，到可见手绘笔触，再到细密纹理 | 先询问，不默认细腻 |
| 原图保留程度 | 忠于原图 / 适度重构 / 大胆改编 | 决定位置、轮廓、背景及空间关系可改变多少 | 忠于原图，保留主体与主要构图 |
| 色彩倾向 | 原图配色 / 绿蓝自然色 / 柔和暖色 / 自定义 | 决定主色调与辨识性色彩的处理 | 沿用原图配色，做绘画化协调 |
| 光线与情绪 | 原图光线 / 清新日光 / 温柔黄昏 / 静谧月夜 / 自定义 | 决定照明、时段及氛围 | 沿用原图光线与时段 |
| 材质感 | 平整哑光 / 轻微纸纹 / 明显颜料纹理 | 决定表面质感，与笔触精细度分别控制 | 平整哑光水粉质感 |
| 画幅 | 原比例 / 方形 / 竖版 / 横版 / 指定比例 | 决定裁切或延展及最终构图 | 原比例 |

把选择写成具体的绘画要求。这些选项描述的是创作方向，图片工具没有对应的精确数值开关；不要编造 dreaminess、brushwork 等字段。

自由描述优先于菜单。接受“强烈梦幻但细腻”“构图忠于原图、笔触松散”等组合，不把梦幻与细腻设为二选一。仅说“更梦幻”时已确定梦幻方向，但不能据此推断笔触；反之同样处理。原图保留程度限定变形范围：强烈梦幻且忠于原图时，在允许范围内增强色彩、光线、材质和既有自然形态的梦境感，不擅自移动主体。

如果选择彼此冲突，例如同时要求原构图完整保留和裁切成会丢失主体的画幅，只问如何取舍，不默默覆盖某项选择。改画幅时优先保住主体，背景延展仅限已有场景；必要时说明裁切或延展方式。

用户明确说“你决定”或要求自主测试时，可自行选择并简短说明所采用参数，无需反复追问；测试选择不能当作用户永久偏好。批量可共用一次选择，除非用户逐图指定。迭代沿用当前参数，用户调整某项时只更新该项。

### 快捷预设

用户可以直接选择完整组合，或自由调整其中任意参数；不自动替用户选预设。已明确单项偏好时，保留其选择，不用预设覆盖。

| 预设 | 梦幻 | 笔触 | 原图保留 | 配色 | 光线 | 材质 | 画幅 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 自然细腻 | 轻微 | 细腻 | 忠于原图 | 原图配色 | 原图光线 | 平整哑光 | 原比例 |
| 梦幻松散 | 强烈 | 松散 | 适度重构 | 绿蓝自然色 | 原图光线 | 平整哑光 | 原比例 |
| 梦幻细腻 | 强烈 | 细腻 | 适度重构 | 绿蓝自然色 | 原图光线 | 平整哑光 | 原比例 |

用户拿不准时，讲清画面会有什么不同，或用他们上传的参考图解释。不用再追加一轮选项。

## 输入与工具

- 已有明确目标图片时，在偏好已确定后处理。没有目标图时请用户上传；不要用自制图冒充用户照片。用户明确要求自主测试时，可自制测试图并说明来源；测试方向需明确记录。
- 多图时区分“待改画原图”和“风格参考”。目标不明确且影响结果时，只问哪张需要改画。明确要求批量时逐张处理。
- 使用内置 image_gen / image_gen.imagegen（编排工具中可能名为 image_gen__imagegen），不以滤镜、SVG 或文字提示词代替实际改画。工具不可用时如实报告，不宣称已经生成，不擅自切换收费 API。
- 本地图先用 view_image 查看，再用 referenced_image_paths 传入完整路径；只有会话图片没有本地路径时，使用能覆盖所有目标图的最小 num_last_images_to_include，最多五张。两种输入方式不要混用。无法覆盖所有目标时请用户重新附图。
- 首次改画以原图为编辑目标。用户满意后只调整局部或某项参数时，以最新满意结果为编辑目标；原图可作为身份、物件与场景的辅助核对输入，明确两者角色。用户要求从头重画时才重新以原图为目标。
- 透明输入默认保留透明背景；普通照片使用不透明背景，正确设置 transparent_background。

## 风格与保留内容

选择风格参考、设计具体梦幻变化或检查风格偏差时读取 [references/style-guide.md](references/style-guide.md)。优先使用用户提供的作品；未提供时可查阅可访问的艺术家或画廊作品图，实际查看后再用作风格输入。无法获取时用文字指导，不假装用过参考图。

以下是本 skill 的提示设计，结合艺术家官网和合作画廊资料整理，不是对所有作品的固定定义：

- **情绪**：安静、温柔，让环境承载情绪；根据梦幻程度增加梦境感，避免擅自转为戏剧性奇幻效果。
- **色彩**：按已选色彩倾向处理。有植物且选择绿蓝自然色时，可使用层次丰富的草绿、翠绿与深绿，配柔和蓝色。默认保留主体辨识性色彩；自定义配色以用户要求为准，不把每张图都刷成同一种绿。
- **画法**：水粉或丙烯水粉的哑光颜料感、温和边缘与可见手绘材质，重绘整张图而非覆盖纹理滤镜。松散笔触用概括色块与简化细节，不逐根描画草叶；适中保留可见手绘笔触和适量细节；细腻才强调细密草叶、物体纹理与细节。梦幻程度不改变所选笔触精细度。平整哑光、纸纹或明显颜料纹理按材质选择处理；明显纹理不自动等于厚重油画堆积。
- **超现实变化**：已有草、叶、水面可呈现波浪、布料褶皱或流动节奏。随梦幻程度增强变化与空间想象，幅度受原图保留程度约束。忠于原图时保留主体、关键物件与构图；适度重构可调整背景和次要形态；大胆改编可重组空间与自然形态，但保留用户要求的身份特征与关键物件。只改变已授权部分，不擅自新增主体、不照搬具体作品构图。
- **适配原图**：人像保留可辨认特征、姿态和服装；宠物保留花色、形态；城市、室内的改动遵循原图保留程度。原图没有森林，不擅自改成森林。

先看原图，记住需要保留的主体、姿态、位置、衣物、物件和构图，并以用户的要求为准。人像可以有绘画变化，不承诺身份特征或每个像素都不变。

开画前用一句话说清准备怎么改，说完就画，不再多问一次确认。明显或强烈的梦幻感要让人看得见，比如山坡卷起、树冠像帷幔流动。柔光和雾气本身不够。笔触也要体现在草叶、树冠、地面这些具体地方。

## 提示模板

替换槽位，将已选参数和未指定项的默认处理转为一致的画面要求。保留清单与允许改变的范围分别列清；禁止把允许改变的元素同时写进不可变清单。

可组合的提示片段：

- 明显或强烈梦幻：flowing dreamlike natural forms, imaginative spatial relationships within the allowed reconstruction level。
- 松散笔触：looser expressive gouache brushwork, simplified details, broad intentional color shapes; avoid meticulous blade-by-blade foliage。
- 细腻笔触：fine directional grass and leaf strokes where present, carefully rendered textures and retained detail。
- 轻微纸纹：subtle paper grain without obscuring the painted forms。
- 静谧月夜：quiet moonlit atmosphere, coherent cool illumination and softly subdued shadows。

~~~text
Use case: style-transfer
Input images: Image 1 is the edit target. [On first conversion: original image. On a local revision: latest accepted painting. Identify any original identity/scene reference and separate artwork style references by index.]
Primary request: Repaint the image as a painting in the style of Mulgil Kim (Kim Mulgil, 김물길), adapting the serene, nature-led visual language to the following choices.
Dreamlike intensity: [user's choice and concrete visual treatment].
Concrete transformation: [existing element to change, its new visible form, and the allowed extent; do not rely only on blur or glow].
Brushwork/detail: [user's choice, controlled independently of dreamlike intensity].
Reconstruction: [fidelity level; allowed changes].
Must preserve: [subject identity cues, key objects and relationships required by user or fidelity level].
Style/medium: Matte gouache / acrylic-gouache painting with [chosen surface texture]. Repaint the whole image rather than adding a texture filter.
Palette: [chosen palette; original colors if unspecified].
Lighting/mood: [chosen lighting, time and emotion; original lighting if unspecified].
Composition/aspect ratio: [chosen framing and ratio; original ratio if unspecified; crop or extension treatment if applicable].
Style references: [observed transferable color/shape/texture relationships from actual reference images; omit when none are supplied]. Do not copy their figures, objects, scene layout or signature. User-selected brushwork takes priority over the reference's detail level.
Avoid: photorealistic finish, glossy 3D rendering, unintended heavy impasto, thick cartoon outlines, unintended text, watermark, artist signature, extra subjects, changes outside the allowed reconstruction scope; [exclusions appropriate to chosen brushwork].
~~~

用户提供具体画作作为风格参考时，该图只指导颜色、笔触和氛围，主体与场景来自待改画原图。原图有用户要求保留的文字时，在提示中单独列出。

## 用户满意后的局部修改

“这张很好，只把笔触放松”属于修改当前结果，不是重新生成另一幅场景。沿用已选参数，仅更新被点名的部分；提示应列清“改变什么”和“其余保持什么”，例如松散化植物与地面笔触，保留人物、现有梦幻形态、色彩、光线与画幅。使用最新满意图作为编辑目标，必要时用原图辅助核对；两图在提示中明确角色。

保存为新版本，不覆盖满意图。不承诺像素级不变，查看是否发生额外变化；若其他区域明显漂移，针对漂移修正一次。不要把重试后的不满意图自动设为新的满意基准。

## 检查与交付

查看输出，与原图比较主体、关键物件、构图、绘画质感，并检查是否符合本次参数：梦幻程度、笔触、保留范围、配色、光线、材质与画幅。不用随意的相似度百分比宣称客观效果。明显丢失主体、变更关键物件、仍像照片或偏离选定方向时，可针对具体问题修正一次；重复失败时说明实际限制，不无限重试。重试时重申保留清单和已选参数，不重复问同一个问题。

重点分别看：梦幻变化是否实际出现、松散与细腻是否表现在笔触与细节上、参考图的风格关系是否呈现而没有搬入其中对象。局部修改还要与满意图比较未要求改变的区域。


直接展示图片并简短说明实际参数；需要选择或比较时，可并列展示原图与结果，不擅自额外生成版本。需项目保存时，把工具返回的实际文件复制到项目，使用新文件名、保留原图；不假设内置工具支持指定输出路径。提供结果链接，记录实际参数、提示词与使用内置工具的事实，不把未实测的参数效果写成已经验证。描述为 AI 改画，不作为艺术家本人作品。

## 风格依据

首版整理日期：2026-10-08。以下资料提供自然主题、水粉媒介、绿蓝色与轻微超现实的依据；具体提示和默认强度为本 skill 的设计选择。

- [艺术家官网](https://www.kimmulgil.com/) 与 [作品页](https://www.kimmulgil.com/World)：身份与水粉、水彩媒介。
- [Maddox Gallery 艺术家介绍](https://maddoxgallery.com/collections/mulgil-kim/)：自然主题与绿色。
- [Green Melody, Blue Poem 展览](https://maddoxgallery.com/pages/exhibition/mulgil-kim-green-melody-blue-poem)：绿蓝色与宁静氛围。
- [画廊的超现实艺术介绍](https://maddoxgallery.com/blogs/news/5-contemporary-surrealist-artists)：自然形态的梦境变化。
