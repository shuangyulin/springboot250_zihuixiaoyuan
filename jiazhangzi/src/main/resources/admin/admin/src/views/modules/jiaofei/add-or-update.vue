<template>
    <div class="addEdit-block">
        <el-form
                class="detail-form-content"
                ref="ruleForm"
                :model="ruleForm"
                :rules="rules"
                label-width="auto"
                :style="{backgroundColor:addEditForm.addEditBoxColor}">
            <el-row>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng'">
                    <el-form-item class="select" v-if="type!='info'"  label="家长学生" prop="jiazhangxueshengId">
                        <el-select v-model="ruleForm.jiazhangxueshengId" :disabled="ro.jiazhangxueshengId" filterable placeholder="请选择家长学生" @change="jiazhangxueshengChange">
                            <el-option
                                    v-for="(item,index) in jiazhangxueshengOptions"
                                    v-bind:key="item.id"
                                    :label="item.jiazhangxueshengUuidNumber"
                                    :value="item.id">
                            </el-option>
                        </el-select>
                    </el-form-item>
                </el-col>

                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="家长姓名" prop="jiazhangxueshengJiazhangname">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengJiazhangname"
                                  placeholder="家长姓名" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="家长姓名" prop="jiazhangxueshengJiazhangname">
                            <el-input v-model="ruleForm.jiazhangxueshengJiazhangname"
                                      placeholder="家长姓名" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="家长联系方式" prop="jiazhangxueshengPhone">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengPhone"
                                  placeholder="家长联系方式" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="家长联系方式" prop="jiazhangxueshengPhone">
                            <el-input v-model="ruleForm.jiazhangxueshengPhone"
                                      placeholder="家长联系方式" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="学号" prop="jiazhangxueshengUuidNumber">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengUuidNumber"
                                  placeholder="学号" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="学号" prop="jiazhangxueshengUuidNumber">
                            <el-input v-model="ruleForm.jiazhangxueshengUuidNumber"
                                      placeholder="学号" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="学生姓名" prop="jiazhangxueshengXuesheng">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengXuesheng"
                                  placeholder="学生姓名" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="学生姓名" prop="jiazhangxueshengXuesheng">
                            <el-input v-model="ruleForm.jiazhangxueshengXuesheng"
                                      placeholder="学生姓名" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="学生身份证号" prop="jiazhangxueshengIdNumber">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengIdNumber"
                                  placeholder="学生身份证号" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="学生身份证号" prop="jiazhangxueshengIdNumber">
                            <el-input v-model="ruleForm.jiazhangxueshengIdNumber"
                                      placeholder="学生身份证号" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12" v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="upload" v-if="type!='info' && !ro.jiazhangxueshengPhoto" label="学生头像" prop="jiazhangxueshengPhoto">
                        <img style="margin-right:20px;" v-bind:key="index" v-for="(item,index) in (jiazhangxueshengForm.jiazhangxueshengPhoto || '').split(',')" :src="item" width="100" height="100">
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item v-if="ruleForm.jiazhangxueshengPhoto" label="学生头像" prop="jiazhangxueshengPhoto">
                            <img style="margin-right:20px;" v-bind:key="index" v-for="(item,index) in (ruleForm.jiazhangxueshengPhoto || '').split(',')" :src="item" width="100" height="100">
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="班级" prop="banjiValue">
                        <el-input v-model="jiazhangxueshengForm.banjiValue"
                                  placeholder="班级" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="班级" prop="banjiValue">
                            <el-input v-model="ruleForm.banjiValue"
                                      placeholder="班级" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="年级" prop="jiazhangxueshengNianji">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengNianji"
                                  placeholder="年级" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="年级" prop="jiazhangxueshengNianji">
                            <el-input v-model="ruleForm.jiazhangxueshengNianji"
                                      placeholder="年级" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='jiazhangxuesheng' ">
                    <el-form-item class="input" v-if="type!='info'"  label="联系邮箱" prop="jiazhangxueshengEmail">
                        <el-input v-model="jiazhangxueshengForm.jiazhangxueshengEmail"
                                  placeholder="联系邮箱" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="联系邮箱" prop="jiazhangxueshengEmail">
                            <el-input v-model="ruleForm.jiazhangxueshengEmail"
                                      placeholder="联系邮箱" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <input id="updateId" name="id" type="hidden">
            <input id="jiazhangxueshengId" name="jiazhangxueshengId" type="hidden">
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="缴费名称" prop="jiaofeiName">
                       <el-input v-model="ruleForm.jiaofeiName"
                                 placeholder="缴费名称" clearable  :readonly="ro.jiaofeiName"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="缴费名称" prop="jiaofeiName">
                           <el-input v-model="ruleForm.jiaofeiName"
                                     placeholder="缴费名称" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
                <el-col :span="12">
                    <el-form-item class="select" v-if="type!='info'"  label="缴费类型" prop="jiaofeiTypes">
                        <el-select v-model="ruleForm.jiaofeiTypes" :disabled="ro.jiaofeiTypes" placeholder="请选择缴费类型">
                            <el-option
                                v-for="(item,index) in jiaofeiTypesOptions"
                                v-bind:key="item.codeIndex"
                                :label="item.indexName"
                                :value="item.codeIndex">
                            </el-option>
                        </el-select>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="缴费类型" prop="jiaofeiValue">
                        <el-input v-model="ruleForm.jiaofeiValue"
                            placeholder="缴费类型" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="缴费金额" prop="shangdianShouyinTruePrice">
                       <el-input v-model="ruleForm.shangdianShouyinTruePrice"
                                 placeholder="缴费金额" clearable  :readonly="ro.shangdianShouyinTruePrice"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="缴费金额" prop="shangdianShouyinTruePrice">
                           <el-input v-model="ruleForm.shangdianShouyinTruePrice"
                                     placeholder="缴费金额" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
                <el-col :span="24">
                    <el-form-item v-if="type!='info'"  label="缴费详情" prop="jiaofeiContent">
                        <editor style="min-width: 200px; max-width: 600px;"
                                v-model="ruleForm.jiaofeiContent"
                                class="editor"
                                action="file/upload">
                        </editor>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item v-if="ruleForm.jiaofeiContent" label="缴费详情" prop="jiaofeiContent">
                            <span v-html="ruleForm.jiaofeiContent"></span>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12" v-if="!(sessionTable=='jiaoshi' && type!='info')">
                    <el-form-item class="select" v-if="type!='info'"  label="是否缴费" prop="jiaofeiShifouTypes">
                        <el-select v-model="ruleForm.jiaofeiShifouTypes" :disabled="ro.jiaofeiShifouTypes" placeholder="请选择是否缴费">
                            <el-option
                                v-for="(item,index) in jiaofeiShifouTypesOptions"
                                v-bind:key="item.codeIndex"
                                :label="item.indexName"
                                :value="item.codeIndex">
                            </el-option>
                        </el-select>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="是否缴费" prop="jiaofeiShifouValue">
                        <el-input v-model="ruleForm.jiaofeiShifouValue"
                            placeholder="是否缴费" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
            </el-row>
            <el-form-item class="btn">
                <el-button v-if="type!='info'" type="primary" class="btn-success" @click="onSubmit">提交</el-button>
                <el-button v-if="type!='info'" class="btn-close" @click="back()">取消</el-button>
                <el-button v-if="type=='info'" class="btn-close" @click="back()">返回</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>
<script>
    import styleJs from "../../../utils/style.js";
    // 数字，邮件，手机，url，身份证校验
    import { isNumber,isIntNumer,isEmail,isPhone, isMobile,isURL,checkIdCard } from "@/utils/validate";
    export default {
        data() {
            return {
                addEditForm:null,
                id: '',
                type: '',
                sessionTable : "",//登录账户所在表名
                role : "",//权限
                userId:"",//当前登录人的id
                jiazhangxueshengForm: {},
                ro:{
                    jiazhangxueshengId: false,
                    jiaofeiName: false,
                    jiaofeiTypes: false,
                    shangdianShouyinTruePrice: false,
                    jiaofeiContent: false,
                    jiaofeiShifouTypes: false,
                    insertTime: false,
                },
                ruleForm: {
                    jiazhangxueshengId: '',
                    jiaofeiName: '',
                    jiaofeiTypes: '',
                    shangdianShouyinTruePrice: '',
                    jiaofeiContent: '',
                    jiaofeiShifouTypes: '',
                    insertTime: '',
                },
                jiaofeiTypesOptions : [],
                jiaofeiShifouTypesOptions : [],
                jiazhangxueshengOptions : [],
                rules: {
                   jiazhangxueshengId: [
                              { required: true, message: '家长学生不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   jiaofeiName: [
                              { required: true, message: '缴费名称不能为空', trigger: 'blur' },
                          ],
                   jiaofeiTypes: [
                              { required: true, message: '缴费类型不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   shangdianShouyinTruePrice: [
                              { required: true, message: '缴费金额不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]{0,6}(\.[0-9]{1,2})?$/,
                                  message: '只允许输入整数6位,小数2位的数字',
                                  trigger: 'blur'
                              }
                          ],
                   jiaofeiContent: [
                              { required: true, message: '缴费详情不能为空', trigger: 'blur' },
                          ],
                   jiaofeiShifouTypes: [
                              { required: true, message: '是否缴费不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   insertTime: [
                              { required: true, message: '录入时间不能为空', trigger: 'blur' },
                          ],
                }
            };
        },
        props: ["parent"],
        computed: {
        },
        created() {
            //获取当前登录用户的信息
            this.sessionTable = this.$storage.get("sessionTable");
            this.role = this.$storage.get("role");
            this.userId = this.$storage.get("userId");


            if (this.role != "管理员"){
            }
            this.addEditForm = styleJs.addStyle();
            this.addEditStyleChange()
            this.addEditUploadStyleChange()
            //获取下拉框信息
                this.$http({
                    url:`dictionary/page?page=1&limit=100&sort=&order=&dicCode=jiaofei_types`,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        this.jiaofeiTypesOptions = data.data.list;
                    }
                });
                this.$http({
                    url:`dictionary/page?page=1&limit=100&sort=&order=&dicCode=jiaofei_shifou_types`,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        this.jiaofeiShifouTypesOptions = data.data.list;
                    }
                });

         this.$http({
             url: `jiazhangxuesheng/page?page=1&limit=100`,
             method: "get"
         }).then(({ data }) => {
             if (data && data.code === 0) {
                this.jiazhangxueshengOptions = data.data.list;
            }
         });

        },
        mounted() {
        },
        methods: {
            // 下载
            download(file){
                window.open(`${file}`)
            },
            // 初始化
            init(id,type) {
                if (id) {
                    this.id = id;
                    this.type = type;
                }
                if(this.type=='info'||this.type=='else'){
                    this.info(id);
                }
                // 获取用户信息
                this.$http({
                    url:`${this.$storage.get("sessionTable")}/session`,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        var json = data.data;
                    } else {
                        this.$message.error(data.msg);
                    }
                });
            },
            jiazhangxueshengChange(id){
                this.$http({
                    url: `jiazhangxuesheng/info/`+id,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        this.jiazhangxueshengForm = data.data;
                    }
                });
            },
            // 多级联动参数
            info(id) {
                let _this =this;
                _this.$http({
                    url: `jiaofei/info/${id}`,
                    method: 'get'
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        _this.ruleForm = data.data;
                        _this.jiazhangxueshengChange(data.data.jiazhangxueshengId)
                    } else {
                        _this.$message.error(data.msg);
                    }
                });
            },
            // 提交
            onSubmit() {
                this.$refs["ruleForm"].validate(valid => {
                    if (valid) {
                        this.$http({
                            url:`jiaofei/${!this.ruleForm.id ? "save" : "update"}`,
                            method: "post",
                            data: this.ruleForm
                        }).then(({ data }) => {
                            if (data && data.code === 0) {
                                this.$message({
                                    message: "操作成功",
                                    type: "success",
                                    duration: 1500,
                                    onClose: () => {
                                        this.parent.showFlag = true;
                                        this.parent.addOrUpdateFlag = false;
                                        this.parent.jiaofeiCrossAddOrUpdateFlag = false;
                                        this.parent.search();
                                        this.parent.contentStyleChange();
                                    }
                                });
                            } else {
                                this.$message.error(data.msg);
                            }
                        });
                    }
                });
            },
            // 获取uuid
            getUUID () {
                return new Date().getTime();
            },
            // 返回
            back() {
                this.parent.showFlag = true;
                this.parent.addOrUpdateFlag = false;
                this.parent.jiaofeiCrossAddOrUpdateFlag = false;
                this.parent.contentStyleChange();
            },
            //图片

            addEditStyleChange() {
                this.$nextTick(()=>{
                    // input
                    document.querySelectorAll('.addEdit-block .input .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.inputHeight
                        el.style.color = this.addEditForm.inputFontColor
                        el.style.fontSize = this.addEditForm.inputFontSize
                        el.style.borderWidth = this.addEditForm.inputBorderWidth
                        el.style.borderStyle = this.addEditForm.inputBorderStyle
                        el.style.borderColor = this.addEditForm.inputBorderColor
                        el.style.borderRadius = this.addEditForm.inputBorderRadius
                        el.style.backgroundColor = this.addEditForm.inputBgColor
                    })
                    document.querySelectorAll('.addEdit-block .input .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.inputHeight
                        el.style.color = this.addEditForm.inputLableColor
                        el.style.fontSize = this.addEditForm.inputLableFontSize
                    })
                    // select
                    document.querySelectorAll('.addEdit-block .select .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.selectHeight
                        el.style.color = this.addEditForm.selectFontColor
                        el.style.fontSize = this.addEditForm.selectFontSize
                        el.style.borderWidth = this.addEditForm.selectBorderWidth
                        el.style.borderStyle = this.addEditForm.selectBorderStyle
                        el.style.borderColor = this.addEditForm.selectBorderColor
                        el.style.borderRadius = this.addEditForm.selectBorderRadius
                        el.style.backgroundColor = this.addEditForm.selectBgColor
                    })
                    document.querySelectorAll('.addEdit-block .select .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.selectHeight
                        el.style.color = this.addEditForm.selectLableColor
                        el.style.fontSize = this.addEditForm.selectLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .select .el-select__caret').forEach(el=>{
                        el.style.color = this.addEditForm.selectIconFontColor
                        el.style.fontSize = this.addEditForm.selectIconFontSize
                    })
                    // date
                    document.querySelectorAll('.addEdit-block .date .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.dateHeight
                        el.style.color = this.addEditForm.dateFontColor
                        el.style.fontSize = this.addEditForm.dateFontSize
                        el.style.borderWidth = this.addEditForm.dateBorderWidth
                        el.style.borderStyle = this.addEditForm.dateBorderStyle
                        el.style.borderColor = this.addEditForm.dateBorderColor
                        el.style.borderRadius = this.addEditForm.dateBorderRadius
                        el.style.backgroundColor = this.addEditForm.dateBgColor
                    })
                    document.querySelectorAll('.addEdit-block .date .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.dateHeight
                        el.style.color = this.addEditForm.dateLableColor
                        el.style.fontSize = this.addEditForm.dateLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .date .el-input__icon').forEach(el=>{
                        el.style.color = this.addEditForm.dateIconFontColor
                        el.style.fontSize = this.addEditForm.dateIconFontSize
                        el.style.lineHeight = this.addEditForm.dateHeight
                    })
                    // upload
                    let iconLineHeight = parseInt(this.addEditForm.uploadHeight) - parseInt(this.addEditForm.uploadBorderWidth) * 2 + 'px'
                    document.querySelectorAll('.addEdit-block .upload .el-upload--picture-card').forEach(el=>{
                        el.style.width = this.addEditForm.uploadHeight
                        el.style.height = this.addEditForm.uploadHeight
                        el.style.borderWidth = this.addEditForm.uploadBorderWidth
                        el.style.borderStyle = this.addEditForm.uploadBorderStyle
                        el.style.borderColor = this.addEditForm.uploadBorderColor
                        el.style.borderRadius = this.addEditForm.uploadBorderRadius
                        el.style.backgroundColor = this.addEditForm.uploadBgColor
                    })
                    document.querySelectorAll('.addEdit-block .upload .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.uploadHeight
                        el.style.color = this.addEditForm.uploadLableColor
                        el.style.fontSize = this.addEditForm.uploadLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .upload .el-icon-plus').forEach(el=>{
                        el.style.color = this.addEditForm.uploadIconFontColor
                        el.style.fontSize = this.addEditForm.uploadIconFontSize
                        el.style.lineHeight = iconLineHeight
                        el.style.display = 'block'
                    })
                    // 多文本输入框
                    document.querySelectorAll('.addEdit-block .textarea .el-textarea__inner').forEach(el=>{
                        el.style.height = this.addEditForm.textareaHeight
                        el.style.color = this.addEditForm.textareaFontColor
                        el.style.fontSize = this.addEditForm.textareaFontSize
                        el.style.borderWidth = this.addEditForm.textareaBorderWidth
                        el.style.borderStyle = this.addEditForm.textareaBorderStyle
                        el.style.borderColor = this.addEditForm.textareaBorderColor
                        el.style.borderRadius = this.addEditForm.textareaBorderRadius
                        el.style.backgroundColor = this.addEditForm.textareaBgColor
                    })
                    document.querySelectorAll('.addEdit-block .textarea .el-form-item__label').forEach(el=>{
                        // el.style.lineHeight = this.addEditForm.textareaHeight
                        el.style.color = this.addEditForm.textareaLableColor
                        el.style.fontSize = this.addEditForm.textareaLableFontSize
                    })
                    // 保存
                    document.querySelectorAll('.addEdit-block .btn .btn-success').forEach(el=>{
                        el.style.width = this.addEditForm.btnSaveWidth
                        el.style.height = this.addEditForm.btnSaveHeight
                        el.style.color = this.addEditForm.btnSaveFontColor
                        el.style.fontSize = this.addEditForm.btnSaveFontSize
                        el.style.borderWidth = this.addEditForm.btnSaveBorderWidth
                        el.style.borderStyle = this.addEditForm.btnSaveBorderStyle
                        el.style.borderColor = this.addEditForm.btnSaveBorderColor
                        el.style.borderRadius = this.addEditForm.btnSaveBorderRadius
                        el.style.backgroundColor = this.addEditForm.btnSaveBgColor
                    })
                    // 返回
                    document.querySelectorAll('.addEdit-block .btn .btn-close').forEach(el=>{
                        el.style.width = this.addEditForm.btnCancelWidth
                        el.style.height = this.addEditForm.btnCancelHeight
                        el.style.color = this.addEditForm.btnCancelFontColor
                        el.style.fontSize = this.addEditForm.btnCancelFontSize
                        el.style.borderWidth = this.addEditForm.btnCancelBorderWidth
                        el.style.borderStyle = this.addEditForm.btnCancelBorderStyle
                        el.style.borderColor = this.addEditForm.btnCancelBorderColor
                        el.style.borderRadius = this.addEditForm.btnCancelBorderRadius
                        el.style.backgroundColor = this.addEditForm.btnCancelBgColor
                    })
                })
            },
            addEditUploadStyleChange() {
                this.$nextTick(()=>{
                    document.querySelectorAll('.addEdit-block .upload .el-upload-list--picture-card .el-upload-list__item').forEach(el=>{
                        el.style.width = this.addEditForm.uploadHeight
                        el.style.height = this.addEditForm.uploadHeight
                        el.style.borderWidth = this.addEditForm.uploadBorderWidth
                        el.style.borderStyle = this.addEditForm.uploadBorderStyle
                        el.style.borderColor = this.addEditForm.uploadBorderColor
                        el.style.borderRadius = this.addEditForm.uploadBorderRadius
                        el.style.backgroundColor = this.addEditForm.uploadBgColor
                    })
                })
            },
        }
    };
</script>
<style lang="scss">
.editor{
  height: 500px;

  & /deep/ .ql-container {
	  height: 310px;
  }
}
.amap-wrapper {
  width: 100%;
  height: 500px;
}
.search-box {
  position: absolute;
}
.addEdit-block {
	margin: -10px;
}
.detail-form-content {
	padding: 12px;
}
.btn .el-button {
  padding: 0;
}</style>

